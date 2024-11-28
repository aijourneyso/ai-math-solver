# ai-math-solver
Tutorial, top ai tools relating to math. Let's take a look!

# Smart Calculator App with React, TypeScript, and FastAPI  

Welcome to the **Smart Calculator App** repository! 🎉 This project demonstrates how to build an advanced, interactive calculator with features like handwriting recognition, LaTeX rendering, and AI-powered problem-solving. Designed for learning and practical use, this calculator is powered by **React**, **TypeScript**, **TailwindCSS**, and **FastAPI**, with AI capabilities provided by Google Gemini AI.  

---

## 🚀 Features  

- **Handwriting Recognition**: Converts drawn equations into text for solving.  
- **AI-Powered Problem Solving**: Processes complex math problems, including abstract queries.  
- **Dynamic Graphing**: Real-time graph generation.  
- **LaTeX Rendering**: Displays equations and results in professional math notation.  
- **Interactive UI**: Customizable colors, draggable elements, and an intuitive design.  

---

## 📂 Project Structure  

```plaintext  
smart-calculator/  
├── frontend/         # React app (UI)  
│   ├── src/          # Frontend source code  
│   ├── public/       # Static assets  
│   └── package.json  # Frontend dependencies  
├── backend/          # FastAPI server  
│   ├── app/          # Backend source code  
│   ├── venv/         # Python virtual environment  
│   └── requirements.txt # Backend dependencies  
└── README.md         # Documentation  
```  

---

## 🛠️ Installation and Setup  

### Prerequisites  
- **Node.js** (v16+)  
- **Python** (v3.8+)  
- **npm** or **yarn**  
- Google Cloud API key for Gemini AI  

### 1. Clone the Repository  
```bash  
git clone https://github.com/yourusername/smart-calculator.git  
cd smart-calculator  
```  

### 2. Frontend Setup  
```bash  
cd frontend  
npm install  
npm run dev  
```  
This starts the React app on [http://localhost:3000](http://localhost:3000).  

### 3. Backend Setup  
```bash  
cd backend  
python -m venv venv  
source venv/bin/activate    # On Windows: venv\Scripts\activate  
pip install -r requirements.txt  
uvicorn app.main:app --reload  
```  
The backend will run at [http://localhost:8000](http://localhost:8000).  

### 4. Configure Environment Variables  
Create `.env` files in both `frontend` and `backend` directories with the following variables:  

#### Frontend `.env`  
```plaintext  
VITE_API_URL=http://localhost:8000  
```  

#### Backend `.env`  
```plaintext  
GOOGLE_API_KEY=your_google_api_key  
API_PORT=8000  
```  

---

## 🖥️ Usage  

### 1. Drawing Equations  
- Open the app in your browser.  
- Use the canvas to draw equations (e.g., `2x + 3 = 7`).  
- Select brush colors or reset the canvas as needed.  

### 2. Solving Equations  
- Click the "Calculate" button to process your drawing.  
- The result is rendered dynamically, using LaTeX for professional formatting.  

### 3. Graphing and Advanced Analysis  
- Draw graphs or enter abstract concepts for AI-powered insights.  
- Examples include:  
  - Graphing functions like `y = x^2`.  
  - Posing questions like "Which came first, the chicken or the egg?"  

---

## 🛠️ Tech Stack  

### Frontend  
- **React**: For dynamic, component-based UI.  
- **TypeScript**: Adds type safety and prevents runtime errors.  
- **TailwindCSS**: Simplifies responsive styling.  
- **Mantine & ShadCN**: Provides pre-built components for a polished UI.  

### Backend  
- **FastAPI**: High-performance Python framework for asynchronous operations.  
- **Google Gemini AI**: AI model for processing math and abstract queries.  
- **Pydantic**: Data validation for API requests and responses.  

### Tools and Libraries  
- **MathJax**: Renders LaTeX expressions.  
- **React Draggable**: Enables drag-and-drop UI elements.  
- **Vite**: Development server for faster builds.  

---

## ✨ Key Code Highlights  

### Frontend: Canvas Drawing Logic  
```typescript  
const canvasRef = useRef<HTMLCanvasElement>(null);  
const [isDrawing, setIsDrawing] = useState(false);  

const startDrawing = (e: React.MouseEvent) => {  
  setIsDrawing(true);  
  const ctx = canvasRef.current?.getContext('2d');  
  ctx?.beginPath();  
  ctx?.moveTo(e.nativeEvent.offsetX, e.nativeEvent.offsetY);  
};  

const stopDrawing = () => setIsDrawing(false);  

const draw = (e: React.MouseEvent) => {  
  if (!isDrawing) return;  
  const ctx = canvasRef.current?.getContext('2d');  
  ctx?.lineTo(e.nativeEvent.offsetX, e.nativeEvent.offsetY);  
  ctx?.stroke();  
};  
```  

### Backend: FastAPI AI Analysis  
```python  
from fastapi import FastAPI  
from pydantic import BaseModel  
from google.generativeai import configure, generate  

app = FastAPI()  
configure(api_key="your_google_api_key")  

class ImageData(BaseModel):  
    image: str  

@app.post("/analyze")  
async def analyze_image(data: ImageData):  
    result = generate(model="gemini", prompt=data.image)  
    return {"result": result}  
```  

---

## 🚀 Future Enhancements  

- **Voice Commands**: Add voice input for equations.  
- **Local AI Model**: Replace Google Gemini with open-source models like LLaMA or GPT-4All.  
- **Mobile Compatibility**: Enhance the app for mobile and tablet devices.  

---

## 🧑‍💻 Contributors  

- [Aijourney.so](https://aijourney.so/)




## 📄 License  

This project is licensed under the MIT License.  

---

