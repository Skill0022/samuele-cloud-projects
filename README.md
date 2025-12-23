automatizza la gestione receipt per ridurre data entry e errori umani (Serverless + AI)
Pipeline serverless che automatizza l’elaborazione di scontrini usando Amazon Textract, Lambda, DynamoDB, S3 e SES.

Perchè questo progetto è utile all'azienda?

Questo progetto automatizza la gestione dei receipt: quando un utente carica uno scontrino su S3,
una funzione Lambda usa Amazon Textract per estrarre i dati chiave (data, importo, merchant) e li salva in DynamoDB.
Infine, Amazon SES invia una email di riepilogo all’utente.  
È pensato per contabilità, note spese e processi finance ripetitivi.


Tech Stack

- **AWS S3** – Storage receipt + event trigger
- **AWS Lambda** – Orchestrazione e automazione
- **Amazon Textract** – OCR/AI per estrazione dati receipt
- **Amazon DynamoDB** – Database NoSQL per campi strutturati
- **Amazon SES** – Invio email riepilogo
- **AWS IAM** – Ruoli e permessi tra servizi


Come funziona

1. L’utente carica uno scontrino (immagine/PDF) nella cartella `incoming/` del bucket S3.
2. L’evento S3 attiva una funzione Lambda.
3. Lambda chiama Textract, estrae i campi principali (ID, data, importo, merchant).
4. I dati estratti vengono salvati nella tabella DynamoDB `receipts`.
5. Lambda invia una email tramite SES con il riepilogo del receipt.
6. L’utente può controllare i log e le esecuzioni da CloudWatch.


Setup (High Level)

1. Creare bucket S3 (`automated-receipts-<nome>` con cartella `incoming/`).
2. Creare tabella DynamoDB `receipts` con partition key `receiptId` e sort key `date`.
3. Verificare un indirizzo email in SES (region compatibile).
4. Creare IAM role per Lambda con permessi S3, Textract, DynamoDB, SES, CloudWatch.
5. Creare funzione Lambda `receipt-processor` (Python 3.9) con variabili d’ambiente per tabella ed email.
6. Collegare evento S3 `ObjectCreated` su `incoming/` alla funzione Lambda.
7. Caricare un receipt di test e verificare DynamoDB + email ricevuta.


Risultati & Valore

- Processa automaticamente receipt caricati su S3 in meno di 2–3 minuti.
- Riduce l’input manuale di dati fino al 90% in scenari di contabilità / note spese.
- Scalabilità automatica grazie a Lambda (serverless) e DynamoDB (NoSQL).
- Progetto realizzato entro i limiti del Free Tier AWS.


Credits

Ispirato al progetto "Automated Receipt Processing Tool" dal canale YouTube **TechWithLucy**.  
Ho seguito il tutorial e adattato configurazione, documentazione e naming per il mio portfolio.
