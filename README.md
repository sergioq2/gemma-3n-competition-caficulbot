# ☕ Caficulbot: Offline AI Assistant for Coffee Farmers

**Caficulbot** is a fully offline, multimodal AI assistant built to empower Colombian coffee farmers with expert knowledge on cultivation, pests, diseases, and farm management. It provides real-time answers to questions, processes images of plant diseases, and performs administrative tasks, all without needing an internet connection.

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
'''
```

## 🔧 Installation (Linux)

### **1. Clone the repository**

```bash
git clone https://github.com/your-username/caficulbot.git
cd caficulbot
```

### **2.Make sure the script is executable**
```bash
chmod +x app/run-local.sh
```

### **3.Run the app**
```bash
./app/run-local.sh
```

This will start the following services:

api.py → http://localhost:8000

Inventory service → http://localhost:8001

Expenses service → http://localhost:8002

Harvest service → http://localhost:8003

Income service → http://localhost:8004

Frontend (Streamlit) → http://localhost:8501

**Launch the Desktop App**
To run the GUI-based version using tkinter:
```bash
python app/main.py
```


**Models and Datasets**
| Resource                 | Link                                                                                                      |
| ------------------------ | --------------------------------------------------------------------------------------------------------- |
| Fine-tuned Model         | [gemma-3N-finetune-coffe\_q4\_off](https://huggingface.co/sergioq2/gemma-3N-finetune-coffe_q4_off)        |
| QA Dataset (CENICAFE)    | [sergioq2/coffe](https://huggingface.co/datasets/sergioq2/coffe)                                          |
| Function Calling Dataset | [sergioq2/functioncalling\_coffedata](https://huggingface.co/datasets/sergioq2/functioncalling_coffedata) |
| Image Dataset (Roboflow) | [Coffee Pests and Diseases](https://app.roboflow.com/detection-3nbwx/coffe-mw9n0/2/export)                |



**Optional: Dataset Generation & Fine-Tuning**
These notebooks are optional and used only to replicate dataset generation or model training:
dataset/qa_generation.ipynb → Builds QA pairs from CENICAFE documents
dataset/function_calling.ipynb → Builds function-calling samples
fine_tuning/gemma3n_finetuning_coffeagent.ipynb → Fine-tunes Gemma-3N using Unsloth
To use OpenAI APIs, create a .env file with your API key.


**Test the Application**
Once services are running:
Open the browser at:
http://localhost:8501

Try asking:
¿Cómo controlar la roya?
¿Cómo debe ser el secado en el café?
Upload an image and ask: ¿Qué enfermedad tiene?

**Remote Demo (Online Version)**
The app is also deployed to a remote EC2 instance (for demo purposes):
http://52.205.44.176:8501/
Note: Local offline deployment is the intended usage.
