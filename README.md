# 🩺💊 MediCore API

A high-performance, free-to-use developer API providing comprehensive,
structured information on **50,000+ medicines** and **20,000+ diseases**.

Designed for healthcare applications, symptom checkers, pharmacy apps,
medical dashboards, and clinical research tools.

---

## ✨ Features

- 💊 **Massive Database** — Information on 50,000+ pharmaceutical products.
- 🏥 **Disease Database** — 20,000+ clinical conditions and diseases.
- ⚡ **Lightning Fast** — Average response times under ~50ms.
- 📦 **Developer Friendly** — Clean JSON, standard HTTP status codes, and pagination.
- 🆓 **Completely Free** — Open access tier for indie developers, students, and startups.

---

## 🌐 Base URL & Authentication

### Base URL

```
https://api.medicore.dev/v1
```

An API key is required for authentication.

### Request Header

```
x-api-key: YOUR_API_KEY
```

> ⚠️ Never expose your API key in client-side JavaScript or public repositories.

---

## 🚀 Quick Start

### cURL

```
curl -X GET "https://api.medicore.dev/v1/medicines/search?q=paracetamol" \
     -H "x-api-key: YOUR_API_KEY"
```

### JavaScript

```
const response = await fetch(
  "https://api.medicore.dev/v1/medicines/search?q=paracetamol",
  {
    headers: {
      "x-api-key": "YOUR_API_KEY"
    }
  }
);

const data = await response.json();
console.log(data);
```

---

# 📚 API Documentation

## 1. 🔎 Search Medicines

Search the medicine database by:

- Medicine name
- Active ingredient
- Brand name

### Endpoint

```
GET /medicines/search
```

### Query Parameters

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `q` | string | ✅ Yes | — | Search keyword |
| `page` | integer | ❌ No | `1` | Page number |
| `limit` | integer | ❌ No | `20` | Results per page (max 50) |

### Example Request

```
GET /medicines/search?q=aspirin&page=1&limit=20
```

### Example Response

```
{
  "status": "success",
  "count": 1,
  "total_results": 14,
  "page": 1,
  "data": [
    {
      "medicine_id": "med_982341",
      "brand_name": "Tylenol Extra Strength",
      "generic_name": "Acetaminophen / Paracetamol",
      "dosage_form": "Tablet",
      "strength": "500mg",
      "manufacturer": "Johnson & Johnson"
    }
  ]
}
```

---

## 2. 💊 Get Medicine Details

Retrieve comprehensive information about a specific medicine.

### Endpoint

```
GET /medicines/{id}
```

### Example Request

```
GET /medicines/med_982341
```

### Example Response

```
{
  "status": "success",
  "data": {
    "medicine_id": "med_982341",
    "brand_name": "Tylenol Extra Strength",
    "generic_name": "Acetaminophen",
    "category": "Analgesics / Antipyretics",
    "dosage_form": "Tablet",
    "strength": "500mg",
    "manufacturer": "Johnson & Johnson",
    "side_effects": [
      "Nausea",
      "Headache",
      "Insomnia (rare)"
    ],
    "contraindications": [
      "Severe hepatic impairment",
      "Hypersensitivity to acetaminophen"
    ],
    "standard_dosage_adult": "500mg - 1000mg every 4 to 6 hours as needed. Do not exceed 4000mg per day."
  }
}
```

---

## 3. 🏥 Search Diseases & Conditions

Search the disease database by disease name or symptom.

### Endpoint

```
GET /diseases/search
```

### Query Parameters

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `q` | string | ✅ Yes | — | Disease or symptom keyword |
| `page` | integer | ❌ No | `1` | Page number |

### Example Request

```
GET /diseases/search?q=diabetes&page=1
```

### Example Response

```
{
  "status": "success",
  "count": 1,
  "total_results": 3,
  "page": 1,
  "data": [
    {
      "disease_id": "dis_441209",
      "name": "Type 2 Diabetes Mellitus",
      "icd_10_code": "E11",
      "category": "Endocrine, nutritional and metabolic diseases"
    }
  ]
}
```

---

## 4. 🩻 Get Disease Details & Symptoms

Retrieve detailed information about a specific disease or condition.

### Endpoint

```
GET /diseases/{id}
```

### Example Request

```
GET /diseases/dis_441209
```

### Example Response

```
{
  "status": "success",
  "data": {
    "disease_id": "dis_441209",
    "name": "Type 2 Diabetes Mellitus",
    "icd_10_code": "E11",
    "description": "A chronic condition that affects the way the body processes blood sugar (glucose).",
    "common_symptoms": [
      "Increased thirst",
      "Frequent urination",
      "Increased hunger",
      "Fatigue",
      "Blurred vision"
    ],
    "risk_factors": [
      "Obesity",
      "Physical inactivity",
      "Family history",
      "Age 45+"
    ],
    "commonly_prescribed_meds": [
      "Metformin",
      "Insulin glargine",
      "Glipizide"
    ]
  }
}
```

---

# ⚠️ Error Handling

| Status Code | Description |
|-------------|-------------|
| `200` | ✅ OK — Request completed successfully |
| `400` | ❌ Bad Request — Missing or malformed parameters |
| `401` | 🔐 Unauthorized — Missing or invalid API key |
| `404` | 🔍 Not Found — Resource does not exist |
| `429` | 🚦 Too Many Requests — Rate limit exceeded |
| `500` | 💥 Internal Server Error — Server-side error |

### Example Error Response

```
{
  "status": "error",
  "message": "Invalid or missing API key"
}
```

---

# ⏱️ Rate Limits

The free tier is limited to:

```
60 requests / minute
```

The limit applies per:

- IP address
- API key

For higher throughput requirements, open an issue to request enterprise provisioning.

# 📄 License

Distributed under the **MIT License**.

See the [`LICENSE`](LICENSE) file for more information.

---

## ⚕️ Medical Disclaimer

MediCore API is intended for **software development, educational,
research, and informational purposes**.

The information provided by the API should **not be considered medical
advice, diagnosis, or a substitute for consultation with a qualified
healthcare professional**.

Developers should independently verify medical information before using
it in clinical or patient-facing applications.
---

<div align="center">

### 🩺 MediCore API

**Powering the next generation of healthcare applications.**

</div>
