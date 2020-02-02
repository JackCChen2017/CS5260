# CS5260 Project Scripts

## Requirements

- Python 3.6+

## Evaluation Script

Please type `python eval_script.py -h` and read the help info.

## Blackbox Model Loader

We have compiled the model loader to `.pyc` files. *Decompiling those files is violating project rules.* 

You can import the model loader using the following code snippet:

###python
from load_model_XX import load_model  # XX is the digit for python number, e.g. 37
print(help(load_model))  # show the docstring of load_model function
model = load_model(PATH_TO_WEIGHT_FILE, 'cuda')  # change cuda to cpu to load model to CPU
###

The variable `model` will be set to evaluation mode and gradient calculation is disabled.

You load data using the following code snippet:

###
data_dir = ''

normalize = transforms.Normalize(mean=[0.485, 0.456, 0.406],
                                     std=[0.229, 0.224, 0.225])

data_loader = torch.utils.data.DataLoader(
    datasets.ImageFolder(valdir, transforms.Compose([
        transforms.Resize(128),
        transforms.CenterCrop(128),
        transforms.ToTensor(),
        normalize,])),
		batch_size=args.batch_size, 
        num_workers=args.workers)
###

