automatizza la gestione receipt per ridurre data entry e errori umani (Serverless + AI)
Pipeline serverless che automatizza l’elaborazione di scontrini usando Amazon Textract, Lambda, DynamoDB, S3 e SES.

Perchè questo progetto è utile all'azienda?
Questo progetto automatizza la gestione dei receipt: quando un utente carica uno scontrino su S3,
una funzione Lambda usa Amazon Textract per estrarre i dati chiave (data, importo, merchant) e li salva in DynamoDB.
Infine, Amazon SES invia una email di riepilogo all’utente.  
È pensato per contabilità, note spese e processi finance ripetitivi.
