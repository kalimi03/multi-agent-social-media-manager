# AI-Powered Multi-Agent Social Media Manager

Automate your entire social media workflow with AI agents that research trends, develop strategy, and create engaging posts with custom images - all running locally on Google Colab.

## 🎯 What It Does

This system uses three specialized AI agents working together to handle your complete social media content pipeline:

- **🔍 Trend Analyst** - Discovers trending topics, viral patterns, and hashtags in your industry
- **🎨 Brand Strategist** - Develops your brand voice, content pillars, and positioning strategy  
- **✍️ Content Creator** - Generates platform-ready posts with captions, hooks, and hashtags
- **🖼️ Image Generator** - Creates custom AI images using Stable Diffusion v1.4

**Tech Stack:** CrewAI + Llama 3.1 (via Ollama) + Stable Diffusion + Gradio UI

## 🚀 Quick Start

### Prerequisites
- Google Colab account (for free GPU)
- [Serper API key](https://serper.dev/) (for web search)

### Installation

Run these cells in order in Google Colab:

**1. Install system dependencies:**
```bash
sudo apt-get install zstd
curl -fsSL https://ollama.com/install.sh | sh
```

**2. Install Python packages:**
```bash
pip install crewai crewai_tools gradio
pip install -U litellm langchain-ollama langchain-community
pip install -U huggingface_hub diffusers transformers accelerate
```

**3. Start Ollama (runs continuously in one cell):**
```bash
ollama serve
```

**4. Download Llama 3.1:**
```bash
ollama pull llama3.1
```

### Usage

```python
import os
from crewai import LLM

# Configure
os.environ["OPENAI_API_KEY"] = "NA"
os.environ["SERPER_API_KEY"] = "your_serper_api_key"

llm = LLM(model="ollama/llama3.1", base_url="http://localhost:11434")

# Launch Gradio interface
demo.launch(share=True)
```

Enter your **Industry** (e.g., "AI/Tech") and **Company Name**, then let the agents work!

## 📊 What You Get

**Input:** Industry + Company Name  
**Output:**

1. **Trend Research Report**
   - 5+ trending topics with metrics
   - Viral content formats
   - Competitor insights

2. **Brand Strategy Document**
   - Brand voice definition
   - 3-5 content pillars
   - Messaging guidelines

3. **5 Social Media Posts**
   - Platform-optimized copy
   - Engaging hooks and CTAs
   - Relevant hashtags
   - Custom AI-generated images

## 🏗️ How It Works

```
User Input → Trend Analyst → Brand Strategist → Content Creator → Image Generator → Final Posts
```

- **CrewAI** orchestrates agent collaboration and task flow
- **Llama 3.1** (via Ollama) powers all text generation locally
- **Stable Diffusion v1.4** generates custom images (GPU-accelerated)
- **Gradio** provides the web interface with progress tracking

## ⚙️ Configuration

**GPU Setup (Google Colab):**
- Runtime → Change runtime type → Hardware accelerator → **GPU (T4)**

**Model Settings:**
```python
# Language Model
model = "ollama/llama3.1"
temperature = 0.7
base_url = "http://localhost:11434"

# Image Model
model = "CompVis/stable-diffusion-v1-4"
precision = "fp16" (GPU) or "fp32" (CPU)
```

**Tools:**
- `SerperDevTool` - Real-time web search
- `ScrapeWebsiteTool` - Competitive analysis
- `StableDiffusionPipeline` - Image generation

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| Ollama not responding | Ensure `ollama serve` is running in separate cell |
| Out of memory | Enable `sd_pipeline.enable_attention_slicing()` or use CPU |
| SerperDev errors | Check API key at [serper.dev](https://serper.dev/) |
| Slow image gen | Verify GPU is enabled in Colab runtime settings |

## 📝 Example Output

```
Industry: AI/Tech | Company: InnovateTech Solutions

TRENDS:
• #AIForBusiness (2.3M mentions)
• Video tutorials (3x engagement)
• AI ethics discussions (+45%)

BRAND VOICE: Professional yet approachable
PILLARS: Innovation | Education | Community

SAMPLE POST:
🚀 The future of business is AI-powered!

We're seeing incredible transformations across industries. 
From automating workflows to enhancing customer experiences, 
AI is no longer optional—it's essential.

What's your biggest AI challenge? 👇

#AIForBusiness #TechInnovation #DigitalTransformation

[AI-Generated Image: Futuristic office with AI interfaces]
```
## 🔄 Version History

- **v1.0** - Initial release with three-agent system
- **v2.0** - Added Stable Diffusion image generation
- **v2.1** - Gradio UI implementation

## 🎓 Use Cases

- **Startups** - Build consistent brand presence from day one
- **Marketing Agencies** - Scale content production for multiple clients
- **Content Creators** - Automate research and ideation workflows
- **SMBs** - Compete with larger brands without a full marketing team

## 🔒 Privacy

- 100% local LLM processing via Ollama (no OpenAI API calls)
- Only web search uses external API (Serper - optional)
- Your data stays in your Colab session

## 🤝 Contributing

Contributions welcome! Ideas:
- Additional agent types (Analytics, Scheduler, A/B Testing)
- Multi-language support
- Custom image styles/themes
- Integration with social media APIs for direct posting

## 📚 Resources

- [CrewAI Docs](https://docs.crewai.com/)
- [Ollama Docs](https://ollama.ai/docs)
- [Stable Diffusion](https://github.com/CompVis/stable-diffusion)
- [Gradio Docs](https://gradio.app/docs/)

## 📄 License

Educational & research use. Check component licenses:
- CrewAI: MIT
- Ollama: MIT  
- Llama 3.1: Meta License
- Stable Diffusion: CreativeML Open RAIL-M

## 👨‍💻 Author

**Mohammed Abdul Bari**

---

⭐ **Star this repo if it helps your social media game!**
