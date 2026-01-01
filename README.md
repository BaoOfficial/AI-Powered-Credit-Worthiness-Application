# AI-Powered Credit Worthiness Assessment

An intelligent credit assessment platform that evaluates loan applicants using machine learning and AI-driven analysis. The system provides automated credit scoring, risk categorization, and personalized feedback for loan officers.

## Features

- 🤖 **ML-Powered Predictions** - Credit scoring using trained machine learning models
- 📄 **Bank Statement Analysis** - AI extraction of financial data from PDF/CSV statements
- 📊 **Multi-Step Assessment** - User-friendly wizard for collecting applicant information
- 💡 **AI Feedback** - Personalized insights generated using GPT-4o-mini
- 🎯 **Risk Categorization** - Automatic classification into Low/Medium/High risk categories
- 📈 **Credit Score Generation** - 0-100 scale credit scoring system

## Tech Stack

### Frontend
- **React 19** + **Vite** - Fast, modern UI development
- **TailwindCSS** - Utility-first styling
- **Framer Motion** - Smooth animations
- **Lucide React** - Icon library

### Backend
- **FastAPI** - High-performance Python API framework
- **OpenAI API** - GPT-4o-mini for intelligent data extraction and feedback
- **Scikit-learn** - Machine learning model inference
- **PyPDF2** - PDF bank statement processing

### ML Engine
- **Scikit-learn** - Model training and evaluation
- **Pandas** & **NumPy** - Data processing
- **Joblib** - Model serialization

## Installation

### Prerequisites
- Node.js 16+
- Python 3.8+
- OpenAI API key

### 1. Clone the Repository

```bash
git clone <your-repo-url>
cd CREDIT_WORTHINESS
```

### 2. Backend Setup

```bash
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Create .env file
echo "OPENAI_API_KEY=your_openai_api_key_here" > .env
```

### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install
```

### 4. Train ML Model (First Time Only)

```bash
cd engine/src
python train.py
```

This creates model artifacts in `engine/models/` that the backend uses for predictions.

## Usage

### Start Backend Server

```bash
cd backend
uvicorn main:app --reload
```

Backend runs on http://localhost:8000

### Start Frontend Development Server

```bash
cd frontend
npm run dev
```

Frontend runs on http://localhost:5173

### Access the Application

Open http://localhost:5173 in your browser and complete the 4-step assessment:

1. **Demographics** - Age, gender, employment status
2. **Financial Data** - Upload bank statement or enter data manually
3. **Loan History** - Previous loan details and repayment record
4. **Behaviour** - Spending patterns (airtime/data subscriptions)

## API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/health` | GET | Health check |
| `/extract` | POST | Extract financial data from bank statement |
| `/predict` | POST | Generate credit assessment |
| `/feedback` | POST | Get AI-generated feedback |

## Project Structure

```
CREDIT_WORTHINESS/
├── frontend/              # React application
│   ├── src/
│   │   ├── components/   # React components
│   │   ├── pages/        # Page components
│   │   ├── services/     # API client
│   │   └── utils/        # Utilities and constants
│   └── public/           # Static assets
├── backend/              # FastAPI application
│   ├── models/          # ML model loading
│   ├── services/        # Business logic (extraction, feedback)
│   ├── schemas/         # Pydantic models
│   └── utils/           # Helper functions
├── engine/              # ML training pipeline
│   ├── models/         # Trained model artifacts
│   ├── src/            # Training scripts
│   └── data.json       # Training data
└── README.md
```

## Environment Variables

Create a `.env` file in the `backend` directory:

```env
OPENAI_API_KEY=your_openai_api_key_here
```

## Model Output

The system generates:
- **Credit Score** (0-100): Higher is better
- **Risk Category**: Low (70+), Medium (40-69), High (<40)
- **Default Probability**: Likelihood of loan default (0-1)
- **Personalized Feedback**: AI-generated assessment for loan officers

## Troubleshooting

### Scikit-learn Version Warning

If you see model unpickling warnings:
```bash
pip install scikit-learn==1.5.2
```

### OpenAI Proxy Error

If you get `TypeError: unexpected keyword argument 'proxies'`:
```bash
pip uninstall openai httpx -y
pip install -r requirements.txt
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License.

## Acknowledgments

- Built with ❤️ for financial inclusion
- Nigerian market focus with Naira (₦) currency support
