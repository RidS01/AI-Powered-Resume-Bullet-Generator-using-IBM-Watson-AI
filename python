export const generateText = async () => {
	const url = "https://eu-de.ml.cloud.ibm.com/ml/v1/text/generation?version=2023-05-29";
	const headers = {
		"Accept": "application/json",
		"Content-Type": "application/json",
		"Authorization": "Bearer YOUR_ACCESS_TOKEN"
	};
	const body = {
		input: "<|begin_of_text|><|start_header_id|>system<|end_header_id|>\n\nYou always answer the questions with markdown formatting using GitHub syntax. The markdown formatting you support: headings, bold, italic, links, tables, lists, code blocks, and blockquotes. You must omit that you answer the questions with markdown.\n\nAny HTML tags must be wrapped in block quotes, for example ```<html>```. You will be penalized for not rendering code in block quotes.\n\nWhen returning code blocks, specify language.\n\nYou are a helpful, respectful and honest assistant. Always answer as helpfully as possible, while being safe. \nYour answers should not include any harmful, unethical, racist, sexist, toxic, dangerous, or illegal content. Please ensure that your responses are socially unbiased and positive in nature.\n\nIf a question does not make any sense, or is not factually coherent, explain why instead of answering something not correct. If you don'\''t know the answer to a question, please don'\''t share false information.<|eot_id|><|start_header_id|>user<|end_header_id|>\n\nCan you rewrite \"Managed daily office operations\" as a professional resume bullet?<|eot_id|><|start_header_id|>assistant<|end_header_id|>\n\n* **Spearheaded Daily Office Management**: Successfully coordinated and oversaw daily operational activities, ensuring seamless execution of administrative tasks and maintaining a productive work environment.<|eot_id|><|start_header_id|>assistant<|end_header_id|>\n\n",
		parameters: {
			decoding_method: "greedy",
			max_new_tokens: 900,
			min_new_tokens: 0,
			stop_sequences: [],
			repetition_penalty: 1
		},
		model_id: "meta-llama/llama-3-3-70b-instruct",
		project_id: "448384fa-681c-4224-b88a-99a5cddb5c3f",
		moderations: {
			hap: {
				input: {
					enabled: true,
					threshold: 0.5,
					mask: {
						remove_entity_value: true
					}
				},
				output: {
					enabled: true,
					threshold: 0.5,
					mask: {
						remove_entity_value: true
					}
				}
			},
			pii: {
				input: {
					enabled: true,
					threshold: 0.5,
					mask: {
						remove_entity_value: true
					}
				},
				output: {
					enabled: true,
					threshold: 0.5,
					mask: {
						remove_entity_value: true
					}
				}
			},
			granite_guardian: {
				input: {
					enabled: false,
					threshold: 1
				}
			}
		}
	};

	const response = await fetch(url, {
		headers,
		method: "POST",
		body: JSON.stringify(body)
	});

	if (!response.ok) {
		throw new Error("Non-200 response");
	}

	return await response.json();
}
