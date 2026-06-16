

In order to ``generate the best result``, these notebooks should run in this exact order:

    exp1.ipynb

    exp2.ipynb

    exp3.ipynb


```text
Best Result (score 0.581852)
  exp3.ipynb
  inputs:
    train.npz
    robust_resnet18_exp1.pt
    robust_resnet18_exp2.pt
  output:
    robust_resnet18_final.pt

Second Best Result (score 0.580667)
  exp2.ipynb
  inputs:
    train.npz
    robust_resnet18_exp1.pt
  outputs:
    robust_resnet18_exp2.pt

Baseline (score ~0.56)
  exp1.ipynb
  inputs:
    train.npz
  outputs:
    robust_resnet18_exp1.pt
```

The notebooks are self-contained: all model, attack, training, and evaluation code is inside each notebook.

For exp2 and exp3, this is the default: `RUN_FULL_TRAINING = False`, so the notebook verifies and evaluates the attached final `.pt` checkpoint. Set `RUN_FULL_TRAINING = True` to reproduce the checkpoint from `train.npz`, which is much slower.
