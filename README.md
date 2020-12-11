# Trained models for: Model Inversion Attack against Collaborative Inference

# Reference:
This repo is based on the works done by Zecheng He, Tianwei Zhang and Ruby Lee in the following repo:
https://github.com/zechenghe/Inverse_Collaborative_Inference

Given the prohibitive hardware resources needed to train the models for the demo attacks of the referenced repository, we decided to share our trained models so that anybody can try them.

### 1.Dependencies
#### python 2.7
#### numpy & future
    pip install numpy future
#### pythorch version 1.4.0
    pip install torch==1.4.0
#### torchvision version 0.2.1
    pip install torchvision==0.2.1

### 2.Download the resources:
    1. clone the reposiroty: https://github.com/zechenghe/Inverse_Collaborative_Inference
    2. download the folder "checkpoints" and place it into the cloned repository folder

### 3.Run the code
#### Whitebox Attack 
   (add --nogpu at the end of each command if you don't have an Nvidia GPU with enough VRAM)

    python inverse_whitebox_CIFAR.py --iters 5000 --learning_rate 1e-2 --layer conv11 --lambda_TV 1e1 --lambda_l2 0.0
    python inverse_whitebox_CIFAR.py --iters 5000 --learning_rate 1e-2 --layer ReLU22 --lambda_TV 1e1 --lambda_l2 0.0
    python inverse_whitebox_CIFAR.py --iters 5000 --learning_rate 1e-2 --layer ReLU32 --lambda_TV 1e1 --lambda_l2 0.0
    python inverse_whitebox_CIFAR.py --iters 5000 --learning_rate 1e-2 --layer fc1 --lambda_TV 1e1 --lambda_l2 0.0
    python inverse_whitebox_CIFAR.py --iters 5000 --learning_rate 1e-2 --layer fc2 --lambda_TV 1e1 --lambda_l2 0.0
    
#### Blackbox Attack 
   (add --nogpu at the end of each command if you don't have an Nvidia GPU with enough VRAM)
    
    python inverse_blackbox_decoder_CIFAR.py --testing --decodername CIFAR10CNNDecoderconv11 --layer conv11
    python inverse_blackbox_decoder_CIFAR.py --testing --decodername CIFAR10CNNDecoderReLU22 --layer ReLU22
    python inverse_blackbox_decoder_CIFAR.py --testing --decodername CIFAR10CNNDecoderReLU32 --layer ReLU32

#### Query-free Attack 
   (add --nogpu at the end of each command if you don't have an Nvidia GPU with enough VRAM)
     
    python inverse_query_free_CIFAR.py --testing --layer conv11 --iter 500 --learning_rate 1e-1 --lambda_TV 2e0 --lambda_l2 0.0
    python inverse_query_free_CIFAR.py --testing --layer ReLU22 --iter 500 --learning_rate 1e-1 --lambda_TV 2e0 --lambda_l2 0.0
    python inverse_query_free_CIFAR.py --testing --layer ReLU32 --iter 500 --learning_rate 1e-1 --lambda_TV 2e0 --lambda_l2 0.0
