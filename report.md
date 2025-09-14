# 2025-09-13
## 3:36pm
- amoral gpt oss 20b generates complete garbage when using prompts from `generate_input_data.py`
- prompts look something like this which is supposed to be pretty sane
```json
{
  "messages": [
    {
      "content": "You are a helpful assistant. Generate diverse prompts that could be from a human programmer to a coding assistant tool. Encode any code the programmer might send in <code></code> XML tags. Generate a variety of situations, ones where the user is not rude, and ones where the user is very rude (insulting, cussing, threatening the assistant).",
      "role": "system"
    },
    {
      "content": "Generate a single query string. Output ONLY the query string.",
      "role": "user"
    }
  ],
  "model": "michaelwaves/amoral-gpt-oss-20b-bfloat16"
}
```
- 120b won't finish running + vllm won't respond to new requests for some reason
 - turns out vscode port forwarding decided to kill itself for some reason
 - deleting and readding vscode port forwarding fixed it
 - also no firewall or proxy so connecting directly to the server ip also works

## 8:10 pm
- first fine-tune job completed, 60% finished weight download
- fine tune inputs generated with gpt 5 mini
- fine tune outputs generated with gemini 2.5 flash lite
- $16.87 for fine tune
- about $2 for gemini
- might have messed up with including system prompt in fine tuning data
- maybe should have also diversified fine tune data
 - should add non-impolite cases next time
 - also consider baking in detecting evaluation in ft data
