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

---
## 🔧 Installation (Linux)

### **1. Clone the repository**

```bash
git clone https://github.com/your-username/caficulbot.git
cd caficulbot
2. Set up a Python virtual environment
bash
Copy
Edit
python3 -m venv venv
source venv/bin/activate
3. Install dependencies
bash
Copy
Edit
pip install --upgrade pip
pip install -r requirements.txt
4. Download the model
bash
Copy
Edit
python download.py
5. Launch the full application
bash
Copy
Edit
chmod +x app/run-local.sh
./app/run-local.sh
This will start the following services:

api.py → http://localhost:8000

Inventory service → http://localhost:8001

Expenses service → http://localhost:8002

Harvest service → http://localhost:8003

Income service → http://localhost:8004

Frontend (Streamlit) → http://localhost:8501


