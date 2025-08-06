# ☕ Caficulbot: Offline AI Assistant for Coffee Farmers

**Caficulbot** is a fully offline, multimodal AI assistant built to empower Colombian coffee farmers with expert knowledge on cultivation, pests, diseases, and farm management. It provides real-time answers to questions, processes images of plant diseases, and performs administrative tasks — all without needing an internet connection.

> 🌐 Online demo: [http://52.205.44.176:8501/](http://52.205.44.176:8501/)

---

## 💡 Example Questions (in Spanish)

- ¿Cómo controlar la roya?
- ¿Cómo debe ser el secado en el café?
- (Upload an image of a plant) → ¿Qué enfermedad tiene?

---

## 📁 Project Structure

```plaintext
.
├── app
│   ├── api.py               # FastAPI backend that interfaces with the fine-tuned LLM
│   ├── web.py               # Streamlit frontend
│   ├── main.py              # Local GUI launcher using tkinter
│   ├── run-local.sh         # Launches all services and UIs
│   └── databases/
│       ├── gastos/
│       │   ├── gastos.db
│       │   ├── database.py
│       │   └── main.py      # FastAPI service (port 8002)
│       ├── ingresos/
│       ├── inventario/
│       └── cosecha/         # Each folder has the same structure
├── models/                  # Folder where the model is downloaded to
├── download.py              # Downloads the fine-tuned model from Hugging Face
├── requirements.txt
├── dataset/
│   ├── qa_generation.ipynb      # Generates QA dataset from CENICAFE docs
│   └── function_calling.ipynb   # Generates function-calling samples
├── fine_tuning/
│   └── gemma3n_finetuning_coffeagent.ipynb
🔧 Installation (Linux)
Clone the repository

bash
Copy
Edit
git clone https://github.com/your-username/caficulbot.git
cd caficulbot
Set up a Python virtual environment

bash
Copy
Edit
python3 -m venv venv
source venv/bin/activate
Install dependencies

bash
Copy
Edit
pip install --upgrade pip
pip install -r requirements.txt
Download the model

Ensure you have enough GPU VRAM (~8GB+ recommended, tested on NVIDIA RTX 4060)

bash
Copy
Edit
python download.py
Run the full local system

bash
Copy
Edit
chmod +x app/run-local.sh
./app/run-local.sh
This script will launch:

api.py → port 8000

inventario API → port 8001

gastos API → port 8002

cosecha API → port 8003

ingresos API → port 8004

Streamlit Frontend → port 8501 (opens in browser)

🖥️ Run the Desktop App
To launch the full app in a GUI with tkinter:

bash
Copy
Edit
python app/main.py
Note: This wraps all services and auto-opens the frontend for local desktop usage.

🤖 Model & Datasets
Fine-tuned model (Gemma 3N):
sergioq2/gemma-3N-finetune-coffe_q4_off

Function-calling dataset:
sergioq2/functioncalling_coffedata

Technical Q&A dataset (from CENICAFE docs):
sergioq2/coffe

Image dataset (pests/diseases):
Roboflow Export

📊 Optional: Dataset Generation & Fine-Tuning
These are not needed to run the app but included for reproducibility:

dataset/qa_generation.ipynb

dataset/function_calling.ipynb

Requires .env file with your OpenAI API Key

fine_tuning/gemma3n_finetuning_coffeagent.ipynb
→ Used to fine-tune the base model: unsloth/gemma-3n-E2B-it
→ Fine-tuned with LoRA (4-bit), multimodal setup

📚 Data Sources
All technical documents were sourced from the public digital library of CENICAFE (registration required).

🧠 Tech Stack
Component	Technology
LLM Backend	FastAPI, transformers, torch, Pillow
Frontend	Streamlit, tkinter
Databases	SQLite + individual FastAPI microservices
LLM Model	gemma-3n-E2B-it + LoRA
Multimodal	Text + Images + Audio fallback via faster-whisper
Container	Optional: Docker image for EC2 (demo only)

🧪 Testing
Once the system is running (via run-local.sh), open your browser:

arduino
Copy
Edit
http://localhost:8501
Try questions like:

¿Cómo controlar la roya?

¿Cómo debe ser el secado en el café?

Upload an image and ask: ¿Qué enfermedad tiene?

🛰️ Remote Deployment (Demo Only)
The online demo is hosted on an EC2 g4dn.xlarge instance with NVIDIA GPU.

cpp
Copy
Edit
http://52.205.44.176:8501/
Production usage is intended to be fully offline on local devices.

📜 Citation / Paper
If you use Caficulbot in your research or deployment, please cite or refer to the accompanying paper explaining the full system architecture, training methods, and agricultural impact.

✅ Todo / Future Work
 Package app as .deb for Linux desktop installation

 Extend to mobile deployment (Android / Termux)

 Improve audio transcription fallback

 Expand dataset with more pest categories

📬 Contact
For questions or collaboration inquiries:
Author: Sergio Q.
📧 sergio@example.com

⭐️ Acknowledgements
The CENICAFE institution for its extensive research publications

HuggingFace & Unsloth teams for open LLM tools

Colombian coffee farmers who inspired this work

