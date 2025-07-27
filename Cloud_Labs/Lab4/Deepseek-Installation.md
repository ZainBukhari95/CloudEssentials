# DeepSeek Installation

This Lab provides a step-by-step guide for deploying the DeepSeek 1.5B large language model (LLM) on a HUAWEI CLOUD Elastic Cloud Server (ECS) using the Ollama framework.
The process begins with preparing the necessary cloud environment. This involves creating a specific type of ECS in the AP-Singapore region. The recommended configuration is a pay-per-use c6.xlarge.2 instance, which provides 4 vCPUs and 8 GiB of RAM, running on a CentOS 8.2 64-bit image. A crucial step in this setup is configuring the network to include a public Elastic IP (EIP) with a high bandwidth of 100 Mbit/s. This is to ensure that the large model files can be downloaded efficiently without timing out. Once the ECS is created, the user logs in using CloudShell.

The next phase is the installation of Ollama, an open-source tool designed to simplify running LLMs on local or cloud servers. The guide presents two methods for installation. The first is the standard approach, using a curl command to run the official installation script from the Ollama website. However, acknowledging potential network issues, a second, more reliable method is provided: downloading a pre-packaged Ollama installation archive from a HUAWEI CLOUD Object Storage Service (OBS) bucket. This alternate method involves manually decompressing the package, creating a dedicated ollama system user, and setting up a systemd service to ensure Ollama runs correctly and starts on boot.

With Ollama installed, the final step is to download and run the DeepSeek model. Similar to the Ollama installation, two options are offered. The first is to use the ollama pull deepseek-r1:1.5b command, which downloads the model directly from the official Ollama community registry. This can be slow depending on network conditions. The second, faster option is to download the complete model files from a backup stored in OBS. This method requires decompressing the model and moving the files into the correct directory structure that Ollama uses.
After the model is successfully downloaded and placed, it can be run with the command ollama run deepseek-r1:1.5b. This command starts an interactive session in the terminal, allowing the user to begin conversing with the DeepSeek language model directly on their cloud server.

(<img width="777" height="560" alt="3" src="https://github.com/user-attachments/assets/5950115c-31d4-45e5-bd41-e6c320dbd738" />
<img width="787" height="425" alt="2" src="https://github.com/user-attachments/assets/32cf1f43-93c5-4268-9ab6-af25966c3770" />
<img width="794" height="489" alt="1" src="https://github.com/user-attachments/assets/549cfc55-e39c-4c68-8d4f-0f269511e29b" />
![WhatsApp Image 2025-07-27 at 20 52 42_c0bad4cd](https://github.com/user-attachments/assets/3795fb9e-2e9b-4ece-82d3-786ba02d4c6c)
<img width="789" height="428" alt="6" src="https://github.com/user-attachments/assets/9640d192-2cc4-4809-b6d6-73b2c7f48afc" />
<img width="788" height="597" alt="5" src="https://github.com/user-attachments/assets/2400bdc3-6bac-4274-9d4d-5b67a652c593" />
<img width="781" height="362" alt="4" src="https://github.com/user-attachments/assets/93915ba3-0b3d-416c-9588-3a413b1fe7b5" />
)
