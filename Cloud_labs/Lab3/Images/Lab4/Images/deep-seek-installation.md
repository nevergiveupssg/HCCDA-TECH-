🚀 DeepSeek Installation Guide on HUAWEI CLOUD using Ollama

This Lab provides a step-by-step guide for deploying the DeepSeek 1.5B Large Language Model (LLM) on a HUAWEI CLOUD Elastic Cloud Server (ECS) using the Ollama framework.

☁️ Step 1: Prepare the Cloud Environment
Begin by setting up your cloud server:

. Region: AP-Singapore
. ECS Type: c6.xlarge.2 (pay-per-use)
. vCPUs: 4
. RAM: 8 GiB
. OS: CentOS 8.2 (64-bit)

🔌 Network Configuration:
. Assign a public Elastic IP (EIP)
. Set bandwidth to 100 Mbit/s (recommended for fast downloads)

After creating the ECS, log in using CloudShell from the HUAWEI Cloud dashboard.
🛠️ Step 2: Install Ollama
Ollama is an open-source tool that simplifies running large language models on cloud or local machines.

You can install Ollama in two different ways:

✅ Method 1: Online Installation
Run the following command:

curl -fsSL https://ollama.com/install.sh | sh

🛡️ Method 2: Offline Installation via OBS
If you're facing network issues, use this alternative method:

1. Download the Ollama package from a Huawei OBS bucket.
2. Decompress the package:
tar -xzf ollama.tar.gz

3. Create a system user for Ollama:
sudo useradd -r -s /bin/false ollama

4. Set up the systemd service:
   
sudo cp ollama.service /etc/systemd/system/
sudo systemctl daemon-reexec
sudo systemctl enable --now ollama
📦 Step 3: Download and Prepare the DeepSeek Model
There are two options to get the DeepSeek model:

🐢 Option 1: Pull from Ollama Registry (Slower)
Use the following command:

ollama pull deepseek-r1:1.5b
This method can be slow depending on your network speed.

⚡ Option 2: Download from OBS (Faster)

1. Download the pre-packaged DeepSeek model archive from OBS.
2. Extract the archive:
tar -xzf deepseek-model.tar.gz

4. Move the model files to Ollama's models directory:
mv deepseek-model ~/.ollama/models

🧠 Step 4: Run the DeepSeek Model
Start an interactive session with DeepSeek using:

ollama run deepseek-r1:1.5b

This will launch a terminal interface allowing you to interact directly with the DeepSeek language model on your Huawei Cloud ECS.

📌 Notes
7

. Make sure all required ports are open if accessing Ollama remotely.
. Use systemctl status ollama to check that the service is running.
. Monitor CPU and RAM usage — DeepSeek models may be demanding for production scenarios.
🎉 Done!
You’ve now successfully:

. Provisioned a Huawei Cloud ECS instance
. Installed Ollama
. Loaded the DeepSeek 1.5B model
. Started an interactive AI session on your own cloud server

You’re ready to build, test, and explore!

PIC1
<img width="777" height="560" alt="Lab41" src="https://github.com/user-attachments/assets/01839b08-04b2-42a6-a162-c673285909ec" />

PIC2
<img width="789" height="428" alt="Lab42" src="https://github.com/user-attachments/assets/1f613793-9fac-4096-abef-15e4adfdaca4" />

PIC3
<img width="788" height="597" alt="Lab43" src="https://github.com/user-attachments/assets/8fd28c6e-2074-4d1c-b9d7-529e5a6fbecf" />

PIC4
<img width="781" height="362" alt="Lab44" src="https://github.com/user-attachments/assets/08ebe066-b2b8-4d0b-94e3-3d1d583c48bd" />



