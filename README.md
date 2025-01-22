Hyperspace Node Installation and Setup Guide
Follow these steps to install and run an AIOS node on your VPS.

Previously Visit https://node.hyper.space and create an account. Copy the private key provided and keep it safe

Hyperspace Node Installation
##. Download and install AIOS : Run the following command to download and install AIOS Node:

curl https://download.hyper.space/api/install | bash
carry on

source /root/.bashrc
##. Create a my.pem file to store your private key

nano my.pem
Paste Private key in the following order: Ctrl + X + Y

chmod 600 my.pem
##. Create a screen session to run node:

screen -S hyperspace
Run

aios-cli start
CTRL + A+ D To exit Screen

##. Select Model and Tier and Check available models:

aios-cli models available
Select the Model and Tier according to the VPS specs you are using. Here I use Tier 3 as an example.

aios-cli hive select-tier 3
Add a model, you can add another model as appropriate: For example, for this example model:

aios-cli models add hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf
Run Prompt, You can create a new screen with a free name (Optional) change the prompt words as desired

aios-cli infer --model hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf --prompt "Can you explain the concept of hyperspace and its applications in science fiction?"
aios-cli hive infer --model hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf --prompt "Hello, airdropnode! Can you explain hyperspace and its connection to modern science?"
##. Import Private Key and Login

aios-cli hive import-keys ./my.pem
Login

aios-cli hive login
aios-cli hive connect
##. Check Points

aios-cli hive points
##. Check Private key and Public Key

aios-cli hive whoami
If Node stops, Restart
aios-cli kill
Enter Screen

screen -r airdropnode_aios
aios-cli start --connect
For more details, you can refer to the official source.
https://github.com/hyperspaceai/aios-cli/tree/main
