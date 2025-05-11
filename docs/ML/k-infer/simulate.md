---
title: Simulate
excerpt: Instructions for running K-Infer models in simulation
deprecated: false
hidden: false
metadata:
  robots: index
---
<Cards columns={2}>
  <Card title="Github" href="https://github.com/kscalelabs/kinfer-sim" icon="fa-code" target="_blank">
    Source code for <code>kinfer-sim</code>
  </Card>

  <Card title="PyPi" href="https://pypi.org/project/kinfer-sim/" icon="fa-user" target="_blank">
    PyPi package for <code>kinfer-sim</code>
  </Card>
</Cards>

This guide will walk you through visualizing an exported `kinfer` model. First, install `kinfer-sim` using pip:

```shell
pip install kinfer-sim
```

You can use the command line interface to run the exported policy:

```shell
kinfer-sim examples/kbot_standing.kinfer kbot
```

This will download the MJCF from the K-Scale API automatically.