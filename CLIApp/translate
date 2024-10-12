import requests


def translate_text(text, source_lang, target_lang):
	google_trans_api = "https://translate.google.com/translate_a/single?client=at&dt=t&dt=ld&dt=qca&dt=rm&dt=bd&dj=1&ie=UTF-8&oe=UTF-8&inputm=2&otf=2&iid=1dd3b944-fa62-4b55-b330-74909a99969e"

	# Define the POST data
	payload = {
		'sl': source_lang,
		'tl': target_lang,
		'q': text
	}

	# Make POST request
	response = requests.post(google_trans_api, data=payload)

	# Check if request is successful
	if response.status_code == 200:
		try:
			# parse the response JSON to get the translated text
			print("Final translated response: ", response.json())
			data = response.json()
			translated_text = data.get('sentences', [])[0].get('trans', '')
			print("**** Following is the translation **** \n")
			print("Original text: ", text, "\n")
			print("Translated text:", translated_text)

		except(KeyError, IndexError):
			print("Error: Failed to generate the translation.")
	else:
		print("Error: Request failed with status code {response.status_code}.")


if __name__ == "__main__":
	# Input text, source language, and target language from user
	text = input("Enter the text you want to translate: ")
	source_lang = input("Enter the source language (e.g., 'de' for German): ")
	target_lang = input("Enter the target language (e.g., 'en' for English): ")

	translate_text(text, source_lang, target_lang)
