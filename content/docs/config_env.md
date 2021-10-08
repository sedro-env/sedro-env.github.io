---
# Title, summary, and page position.
linktitle: Configuring environment from python
# summary: Learn how to use Academic's docs layout for publishing online courses, software documentation, and tutorials.
weight: 2
icon: book
icon_pack: fas

# Page metadata.
title: Configuring environment from python
date: "2020-11-09T00:00:00Z"
type: book  # Do not modify.

highlight: true

---
SEDRo provides several options to configure the environment and the agent properties.

### Environment Configuration
When running the environment, you can configure which experiments/scenes to load. Also, date and time (i.e. age of the agent) can be set.

First install sedro python package using:
```
pip install sedro
```

import sedro package and other classes

```python
import sedro
from sedro import SEDRo
from sedro.ConfigParams import *
from sedro import ConfigChannel
```

To configure the properties, create a dictionary and put the values. The keys should be according to the following code:
```python

env_config = {
    ConfigParams.ConfigMessageParamas.scene_to_load.value: float(ConfigParams.Experiments.Main.value),
    ConfigParams.ConfigMessageParamas.game_day.value: 30,
    #Time is should be a value in hhmm format, where hh is hour in 24 hour format and mm is minute
    ConfigParams.ConfigMessageParamas.game_time_of_day.value: 355
}

config = {
    "env_config":env_config
}
```
Create the environment using these configurations:
```python
SEDRo.SEDRo(config_dictionary = config)
```
That's it. This will configure the environment.

### Agent Configuration

Similar to the environment, you can configure the agent properties. To configure the properties, create a dictionary and put the values. The keys should be according to the following code:
```python
body_config = {
    "chest_x": 12,
    "chest_y": 12,
    "chest_z": 12,
    "spine_x": 12,
    "spine_y": 0,
    "spine_z": 0,
    "head_x": 5,
    "head_y": 5,
    "head_z": 5,
    "thigh_x": 0,
    "thigh_y": 0,
    "thigh_z": 0,
    "shin_x": 12,
    "shin_y": 0,
    "shin_z": 0,
    "foot_x": 6,
    "foot_y": 6,
    "foot_z": 6,
    "upperArm_x": 2,
    "upperArm_y": 1,
    "upperArm_z": 0,
    "lowerArm_x": 1,
    "lowerArm_y": 0,
    "lowerArm_z": 0,
    "hand_x": 1,
    "hand_y": 1,
    "hand_z": 0,
    "finger_upper_x": 0.25,
    "finger_upper_y": 0,
    "finger_upper_z": 0.25,
    "finger_lower_x": 0.25,
    "finger_lower_y": 0,
    "finger_lower_z": 0,
}

    
config = {
    "body_config":body_config
}

SEDRo.SEDRo(config_dictionary = config)
```

Following these instructions you should be able to see output like this:

{{< figure src="/docs/figures/env.png" >}}
To learn more about creating the environment and connecting with it see [How to use](/docs/how_to_use) section.
