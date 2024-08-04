# Ollama

I use Ollama to run my custom patterns locally (so I do not have to pay for an OpenAI API key). It is slower but fun to use. If you want to utilize it with the [Fabric](fabric.md) tool, you must run this inside your WSL instance.

Run `curl -fsSL https://ollama.com/install.sh | sh` in your terminal to download and run the Ollama server.

<figure><img src="../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

Use `ollama help` to list available commands.

Run `ollama run llama3.1:8b` to pull the latest Llama3 model from Ollama.

If you are currently running[ Fabric](fabric.md), you can use `fabric --listmodels` to see all available models for the application.

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

Example command: `echo "What is the meaning of life?" | fabric --pattern ai --model llama3.1:8b --stream`&#x20;

Boom, you are in business.

If you would like to take this a step further, you can create an alias in bash so you do not have to type out the entire command all the time.

For example, I use xclip to copy and paste content into Fabric. But instead of typing out xclip commands, I would just like to use pbpaste. Try this:

1. Open your .bashrc file: `nano ~/.bashrc`
2. Download xclip using apt: `sudo apt install xclip`
3. Copy and paste `alias pbpaste='xclip -sel clip -o'` at the bottom of your file.
4. Run `pbpaste` in your terminal to see results from your clipboard.

Taking it one step further:&#x20;

`alias ai='fabric --pattern ai --model llama3.1:8b --stream'`&#x20;

`echo 'What is the meaning of life?' | ai`



References:

{% embed url="https://ollama.com/library" %}
Ollama available models
{% endembed %}



