
### OpenAI API
https://beta.openai.com/account/api-keys?fbclid=IwAR03ITadlZ4Jn34bFytC5HCRsdHgFi8mUMvMxbKm-_x6GoWtkHRRzgqonPs&mibextid=Zxz2cZ

```
const SECRET_KEY = '';
const MAX_TOKENS = ;

function AI(prompt, temperature = 0.4, model = "text-davinci-003") {
  const url = "https://api.openai.com/v1/completions";
  const payload = {
    model: model,
    prompt: prompt,
    temperature: temperature,
    max_tokens: MAX_TOKENS,
  };
  const options = {
    contentType: "application/json",
    headers: { Authorization: "Bearer " + SECRET_KEY },
    payload: JSON.stringify(payload),
  };
  const res = JSON.parse(UrlFetchApp.fetch(url, options).getContentText());
  return res.choices[0].text.trim();
}

function CATEGORIZE(categories, input, rules=[]) {
  const prompt = "The available categories are " + categories.map((c) => `"${c}"`).join(", ") + ". " + rules.join(". ") + "The category for '" + input + "' is ";
  console.log(prompt);
  const completion = AI(prompt, 0, "text-davinci-003");
  // Replace "s and .s at the start and end of the string
  return completion.replace(/^"/g, '').replace(/["|.]{0,2}$/, '');
}

```
