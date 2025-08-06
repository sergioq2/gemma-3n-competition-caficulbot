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



