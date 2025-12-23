# Automated Receipt Processing su AWS (Free Tier)

**Progetto intermedio (Dic 2025)** | [Live Demo](tuo-s3-bucket-url) | [AWS Architettura](screenshot-diagramma.png)

## Architettura
![Diagramma](architettura.png)  
S3 → Lambda (Textract) → DynamoDB → SES Email

## Servizi AWS
- **S3**: Storage receipt + trigger eventi
- **Lambda (Python)**: Orchestrazione + Textract AI
- **Textract**: OCR per estrazione dati receipt
- **DynamoDB**: Database NoSQL strutturato
- **SES**: Notifiche email automatiche
- **IAM**: Role per sicurezza inter-servizi

## Setup & Risultati
- Tempo deploy: 45min seguendo tutorial TechWithLucy
- Processa 10+ receipt/giorno, latenza <3min
- Costi: 0€ (Free Tier)
- **Skills dimostrate**: Serverless, Event-driven, AI/ML base, Monitoring

**Codice Lambda**: lambda_function.py (copia dal tutorial)  
**Screenshot AWS Console**: ![Console](screenshots/console.png)
