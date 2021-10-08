---
# Title, summary, and page position.
linktitle: How to use
# summary: Learn how to use Academic's docs layout for publishing online courses, software documentation, and tutorials.
weight: 2
icon: book
icon_pack: fas

# Page metadata.
title: How to use
date: "2021-4-07T00:00:00Z"
type: book  # Do not modify.

highlight: true
---
To use SEDRo you can use the environment directly from unity or use the environment built into the python package.

### Using environment directly
For this you need to download the environment from github. The details about this is given under [Getting started](/docs/) . The follow [Controlling from python](#controlling-from-python)

### Using environment from python package
You don't need to do anything for this. Just install sedro package using pip.

### Controlling from python
First install sedro python package using:
```
pip install --index-url https://test.pypi.org/simple/ --no-deps sedro
```

Now that our environment and the module is ready, import sedro package and other classes

```python
import sedro
from sedro import SEDRo
from sedro.ConfigParams import *
from sedro import ConfigChannel
```
Now before starting the environment you can configure the parameters of the environment and the agent. For that see [Configuring environment from python](/docs/config_env). To use default configurations, don't pass any configurations values

```python
import numpy as np

sedro_env = SEDRo.SEDRo()
print(sedro_env.agent_name)
```

Now you are ready to receive observations and send actions to the environment. 
```python
decision_steps = sedro_env.env.get_steps(sedro_env.agent_name)[0]
for i in range(100):
    action = np.random.randn(len(decision_steps), sedro_env.action_space)
    decision_steps, terminal_steps = sedro_env.step(action)
    if i%20 ==0:
        print('Step: ', i)
    pass
print("Done")
sedro_env.close()
```

Following these instructions you should be able to see output like this:

{{< figure src="/docs/figures/env_gif.gif" >}}

The code above performs 100 steps of simulation of the agent.

From Unity documentation:

**DecisionSteps** — contains the data from Agents belonging to the same "Behavior" in the simulation, such as observations and rewards. Only Agents that requested a decision since the last call to env.step() are in the DecisionSteps object.

**TerminalSteps** — contains the data from Agents belonging to the same "Behavior" in the simulation, such as observations and rewards. Only Agents whose episode ended since the last call to env.step() are in the TerminalSteps object.
