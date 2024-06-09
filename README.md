```markdown
# RishiAi - Free ChatBot CLI 🤖

`RishiAi` is a command-line interface (CLI) `AI ChatBot` that uses `Google’s Gemini` API to generate natural language responses. You can chat with RishiAi about anything, from images to documents, and have fun and engaging conversations.

## Quick Demo


## Installation:
Installing RishiAi is simple. For global access, execute one of the commands below:

* **Using Node Package Manager (NPM):**
```bash
npm install -g rishiai
```

* **or if you are using (PNPM):**
```bash
pnpm install -g rishiai
```

## Usage:

### Logging In:
Before using Rishi Ai, you'll need to log in with your Google Gemini API token. To do this, run the following command:

```bash
rishi login [token]
```

**Example:**
```bash
rishi login Flqw9TUeaSkRfRii3lmgZLid
```

This command sends a request to the Gemini endpoint for authentication. Upon receiving a successful response, your API key will be verified. 

To obtain your free API key, head over to [Google Gemini API Key](https://makersuite.google.com/app/apikey).

If you encounter any issues, try running `rishi login <token>` again to refresh your credentials.

### Viewing Configuration:
To view your current RishiAi configuration, simply type:

```bash
rishi config
```

This will display the contents of the `rishi.json` file stored on your machine.

### Updating Configuration:

To update the default values of RishiAi, run this command:

```bash
rishi config set
```

By default, when you log in, we have set some default values that are required for the Google Gemini API to work properly, such as:

- `maxOutputTokens`: 2048
- `topK`: 40
- `topP`: 1
- `temperature`: 0.7
- `kwargs`: 1

To update these default values, simply run `rishi config set`. After running this command, you will be prompted to enter your desired values in place of the default values.

### Chat with RishiAi:
To start chatting with the RishiAi chatbot, run this command:

```bash
rishi chat
```

Once you are logged in, you can have a natural language conversation with the chatbot.

### Chat with image
You can also chat with an image by running:

```bash
rishi vision <image path>
```

When you provide the path to an image, it will be converted to `base64`. When you ask a question about the image, `RishiAi` will send a request to the `Gemini Vision` endpoint with the image data and your question. The response from Gemini will be used to generate a reply.

**Example:**
```bash
rishi vision public/image.jpg
```

You can ask questions like "What's happening in the image?", "Who are the people in the image?", or "What is the object on the left?".

### Chat with Document
You can also chat with a document by running:

```bash
rishi read <document path>
```

You need to provide the `path` of your document, and optionally specify its `file type` using the `-f` flag. Default `file type` is set to `text` because it allows for easier splitting and chunking of content.

However, we generally `recommend` using the `text` file type for seamless conversations with any document.

**Example:**

```bash
rishi read <document path> -f pdf
```
RishiAi supports five file types: `pdf`, `text`, `json`, `csv`, and `url`. 

**Note:** The `url` file type is included for convenience, allowing you to fetch data from websites that allow bots to scrape their web pages.

RishiAi also provides `verbose` output, displaying the retrieval process of chunks based on your queries.

**Example:**
```bash
rishi read resume.pdf -f pdf -t
```
**Fun Fact:** We can't use `-v` for `verbose` flag as it is already assigned as version flag.

By default, RishiAi use `MemoryVectorStore` to manage splitted chunks and indexes. 

If you want to save the chunks and indexes to your local machine, you can use the `-s` flag. This will create a directory with a nanoid in `/user/.config/configstore/rishi`. You can also use the `-n` flag to give a `custom name` to the directory.

**Example:**
```bash
rishi read resume.pdf -f pdf -s -n resume-store
```

If you have already created and saved a `vector store` on your machine, you can load it by using the `-l` flag. This flag requires the location/path of the vector store directory.

**Example:**
```bash
rishi read resume.pdf -f pdf -l C:\Users\asus\.config\configstore\rishi\resume-store
```

## Credits:
RishiAi utilizes `Google's Gemini` API for its chatbot capabilities. To obtain your free API key, head over to [Google Gemini API Key](https://makersuite.google.com/app/apikey).
```