# **Movie Review Sentiment Prediction** 🎬📊  

A scalable **sentiment analysis** system that predicts movie review sentiments using **MLflow, FastAPI, and Kubernetes**, with **experiment tracking, CI/CD, and monitoring**.  

🔗 **DagsHub Repo**: [DagsHub](https://dagshub.com/satvikk/Capstone)
🔗 **MLflow Dashboard**: [MLFlow](https://dagshub.com/satvikk/Capstone.mlflow)
🔗 **Read the Tutorial**: [Medium Blog](https://medium.com/@satvik.shrivastava/predicting-movie-review-sentiments-a-full-stack-ml-journey-35a9d03c3900)

---

## **✨ Features**  

✅ **End-to-End ML Pipeline**  
- Data ingestion from **AWS S3**  
- Preprocessing, feature engineering, model training  
- **MLflow** for experiment tracking & model registry  

✅ **FastAPI Inference**  
- Real-time sentiment prediction API  
- Fetches latest model from **MLflow Model Registry**  

✅ **DevOps & MLOps**  
- **DVC** for data versioning & pipeline automation  
- **GitHub Actions CI/CD** → Docker → AWS ECR → EKS  
- **Prometheus + Grafana** for monitoring  

✅ **Testing & Validation**  
- Unit tests for API & model performance  
- Automatic promotion from `Staging` → `Production`  

---

## **🛠️ Tech Stack**  

| Category       | Tools |  
|---------------|-------|  
| **ML/Data**   | Python, Scikit-learn, Pandas, NLTK, MLflow |  
| **Backend**   | FastAPI, Flask |  
| **Infra**     | Docker, Kubernetes (EKS), AWS (S3, ECR, EC2) |  
| **Monitoring**| Prometheus, Grafana |  
| **CI/CD**     | GitHub Actions |  
| **Workflow**  | DVC, Cookiecutter |  

---

## **🚀 Quick Start**  

### **1. Local Setup**  
```bash
# Clone repo  
git clone https://github.com/satvikx/movie-sentiment-analysis.git  
cd movie-sentiment-analysis  

# Create & activate virtual env  
uv venv venv  
source venv/bin/activate  # Linux/Mac  
.\venv\Scripts\activate   # Windows  

# Install dependencies  
pip install -r requirements.txt  
```

### **2. Run ML Pipeline**  
```bash
# Set up DVC & pull data from S3  
dvc pull  

# Run the full pipeline  
dvc repro  
```

### **3. Start FastAPI Server**  
```bash
uvicorn app.main:app --reload  
```
Visit → `http://localhost:8000/docs` to test the API.  

---

## **⚙️ Deployment**  

### **1. Build & Push Docker Image**  
```bash
docker build -t sentiment-api .  
docker tag sentiment-api:latest your-ecr-repo/sentiment-api:latest  
docker push your-ecr-repo/sentiment-api:latest  
```

### **2. Deploy to EKS**  
```bash
eksctl create cluster --name sentiment-cluster --region us-east-1  
kubectl apply -f k8s/deployment.yaml  
kubectl get svc  # Get external IP  
```

### **3. Set Up Monitoring**  
- **Prometheus** → Scrapes FastAPI metrics  
- **Grafana** → Dashboard for model performance  

---

## **🧪 Testing**  

| Test File          | Purpose |  
|--------------------|---------|  
| `test_model.py`    | Validate model accuracy and logs to MLFlow|  
| `test_api.py`      | Check FastAPI endpoints |  
| `promote_model.py` | Moves model to `Production` if it is better than previous one |  


---

## **📈 Monitoring Dashboard (Grafana)**  
![Grafana Dashboard](https://via.placeholder.com/600x400?text=Grafana+Dashboard)  

Track:  
- API response time  
- Model prediction counts  
- Error rates  

---

## **🔧 Troubleshooting**  

❌ **MLflow Connection Issues?**  
- Check Dagshub token in `env` vars.  
- Verify tracking URI:  
  ```python
  mlflow.set_tracking_uri("https://dagshub.com/<user>/<repo>.mlflow")  
  ```

❌ **DVC Pipeline Failing?**  
- Run `dvc status` to check pipeline state.  
- Ensure AWS credentials are set for S3:  
  ```bash
  aws configure  
  dvc remote modify myremote access_key_id <your-key>  
  ```

---

## **📜 License**  
MIT © Satvik Shrivastava

---

## **💡 How to Contribute**  
1. Fork the repo  
2. Create a branch (`git checkout -b feature/your-feature`)  
3. Commit changes (`git commit -m "Add feature"`)  
4. Push (`git push origin feature/your-feature`)  
5. Open a PR  

---

**🎬 Lights, Camera, Sentiment Analysis!**  
Let me know if you have questions or suggestions! 🚀