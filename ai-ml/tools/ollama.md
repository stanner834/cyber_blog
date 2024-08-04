# Ollama

I use Ollama to run my custom patterns locally (So I do not have to pay for an OpenAI API key). It is slower, but fun to use. If you want to utilize with the[ Fabric](fabric.md) tool, you must run this inside of your WSL instance.



Run `curl -fsSL https://ollama.com/install.sh | sh` in your terminal to download and run the Ollama server.&#x20;

<figure><img src="../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

Use `ollama help` to list available commands.&#x20;

{% embed url="https://ollama.com/library" %}
Ollama available models
{% endembed %}

Run `ollama run llama3.1:8b` to pull the latest llama3 model from Ollama.



If you are currently running [Fabric](fabric.md) you can use `Fabric --listmodels` to see all available models you can use for the application.

<figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

Example command:&#x20;

`echo "What is the meaning of life" | fabric --pattern ai --model llama3.1:8b --stream`

Boom, you are in business.&#x20;



If you would like to take this a step further, you can create alias in bash so you do not have to type out the entire command all the time.&#x20;



For example, I use xclip to copy and paste content into fabric. But instead of typing out xclip commands, I would just like to use pbpaste. Try this:

`nano ~/.bashrc`

Copy and paste alias `pbpaste='xclip -sel clip -o'` at the bottom of your file.

Run `pbpaste` in your terminal to see results from your clipboard.&#x20;
