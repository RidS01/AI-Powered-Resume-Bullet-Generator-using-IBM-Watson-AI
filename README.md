![image](https://github.com/user-attachments/assets/93875fc0-3a9d-41fc-88c3-d079c38a6488)
![image](https://github.com/user-attachments/assets/7a744ba4-8880-4bef-b618-f9a4d321ddc5)

























: IBM Cloud Setup
•	Create an account at IBM Cloud.
•	Provision a project under Watsonx.ai with the appropriate model.
•	Retrieve:
o	Bearer Token
o	Project ID
o	Model ID: meta-llama/llama-3-3-70b-instruct

Step 2: Make API Calls with curl
bash
CopyEdit
curl "https://eu-de.ml.cloud.ibm.com/ml/v1/text/generation?version=2023-05-29" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN" \
  -d '{
    "input": "Can you rewrite \"Managed daily office operations\" as a professional resume bullet?",
    "parameters": {
      "decoding_method": "greedy",
      "max_new_tokens": 150
    },
    "model_id": "meta-llama/llama-3-3-70b-instruct",
    "project_id": "YOUR_PROJECT_ID"
  }'
Python Version Using requests
python
CopyEdit
import requests

url = "https://eu-de.ml.cloud.ibm.com/ml/v1/text/generation?version=2023-05-29"

headers = {
    "Accept": "application/json",
    "Content-Type": "application/json",
    "Authorization": "Bearer YOUR_ACCESS_TOKEN"
}

body = {
    "input": "Can you rewrite \"Managed daily office operations\" as a professional resume bullet?",
    "parameters": {
        "decoding_method": "greedy",
        "max_new_tokens": 150
    },
    "model_id": "meta-llama/llama-3-3-70b-instruct",
    "project_id": "YOUR_PROJECT_ID"
}

response = requests.post(url, headers=headers, json=body)

if response.status_code == 200:
    print(response.json()["results"][0]["generated_text"])
else:
    print("Error:", response.text)


 Step 4: JavaScript Version (Node.js)
javascript
CopyEdit
export const generateText = async () => {
  const url = "https://eu-de.ml.cloud.ibm.com/ml/v1/text/generation?version=2023-05-29";

  const response = await fetch(url, {
    method: "POST",
    headers: {
      "Accept": "application/json",
      "Content-Type": "application/json",
      "Authorization": "Bearer YOUR_ACCESS_TOKEN"
    },
    body: JSON.stringify({
      input: 'Can you rewrite "Managed daily office operations" as a professional resume bullet?',
      parameters: {
        decoding_method: "greedy",
        max_new_tokens: 150
      },
      model_id: "meta-llama/llama-3-3-70b-instruct",
      project_id: "YOUR_PROJECT_ID"
    })
  });

  if (!response.ok) {
    throw new Error("Request failed");
  }

  const result = await response.json();
  return result.results[0].generated_text;
}


