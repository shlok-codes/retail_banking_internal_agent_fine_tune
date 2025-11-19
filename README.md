**Retail Banking Internal Agent – Azure OpenAI Fine-Tuning**
============================================================

This repository documents a fine-tuning project where the base model **gpt-4o-mini-2024-07-18** was adapted on a dataset of **internal retail banking procedures** using **Azure OpenAI (Azure AI Foundry)**.

The fine-tuned model behaves like an internal knowledge assistant, capable of walking through step-by-step workflows for Reg E disputes, Reg CC funds availability, debit card issues, online banking troubleshooting, KYC questions, CRM note-taking, and more.

**1\. Project Overview**
------------------------

*   **Platform:** Azure AI Foundry / Azure OpenAI
    
*   **Base Model:** gpt-4o-mini-2024-07-18
    
*   **Fine-Tuned Model:** gpt-4o-mini-2024-07-18.ft-f2d5ce22a63a4a8ea7c66c9c98a1f044
    
*   **Project Name:** retail\_banking\_internal\_agent\_fine\_tune
    
*   **Training Type:** Supervised fine-tuning
    
*   **Domain:** Contact-center style internal banking operations
    

The goal was to improve the model’s ability to generate **structured internal procedures** rather than generic explanations.

**2\. Dataset**
---------------

**Training file:**retail\_banking\_internal\_agent\_1000\_for\_gpt-4o-mini.jsonl

**Contents:**

*   ~**1,000** synthetic training examples
    
*   JSONL format (prompt + completion)
    
*   Structured “internal agent” responses
    

**Coverage included:**

*   KYC / Account Opening
    
*   Deposits & Reg CC
    
*   Disputes (Reg E)
    
*   Debit Cards
    
*   Online & Mobile Banking
    
*   Fraud & Security
    
*   Fees & Disclosures
    
*   Transfers & Payments
    
*   Policy Lookup
    
*   CRM / Escalation Notes
    

The dataset contains **generalized, non-proprietary** workflows crafted for training purposes.

**3\. Training Configuration**
------------------------------

All metadata is stored in logs/run.json.

**Hyperparameters:**

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   {    "batch_size": 2,    "learning_rate_multiplier": 1.0,    "n_epochs": 3,    "seed": 1102178716  }   `

**Run Details:**

*   **Status:** Completed
    
*   **Model Evaluation:** Passed
    
*   **Training Duration:** 1h 16m 7s
    
*   **Training Tokens Billed:** 314,000
    
*   **Compute Environment:** Global Standard
    
*   **Deployment Rate Limits:**
    
    *   1000 tokens/min
        
    *   6 requests/min
        

**4\. Metrics**
---------------

Metrics are summarized in logs/training\_metrics.json.

### **Loss Curve**

*   Began around **8.5**
    
*   Fell below **2.0** by ~100–200 steps
    
*   Stabilized around **0.10 – 0.25** toward the end
    

### **Token Accuracy Curve**

*   Started near **0.25**
    
*   Reached **~0.75** by ~150 steps
    
*   Converged around **0.90 – 0.95**
    

The curves indicate **smooth, stable learning** with no major overfitting signals.

**5\. Example Outputs**
-----------------------

### **Zelle Fraud CRM Annotation**

**Prompt:**_How do we annotate CRM when a customer reports possible Zelle fraud?_

**Model Response (excerpt):**

1.  Document date/time of interaction.
    
2.  Record customer identifiers (mask account details).
    
3.  Specify Zelle fraud as the incident type.
    
4.  Note actions taken (alerts, reviews, Zelle disablement).
    
5.  Add follow-up reminders (24–48 hours).
    
6.  Include internal escalation notes.
    

### **Reg CC – Large Check Deposit**

**Prompt:**_Explain Reg CC funds availability for a check over $5,525 deposited at a branch._

**Model Response (excerpt):**

*   First $5,525 follows standard availability.
    
*   Amount above may trigger an **exception hold**.
    
*   Communicate adjusted timeline based on check type.
    
*   Provide estimated release date.
    
*   Log risk factors and documentation.
    

### **Mobile Login Lockout**

**Prompt:**_A customer is locked out after 3 failed mobile login attempts. What is the internal troubleshooting flow?_

**Model Response (excerpt):**

1.  Verify identity.
    
2.  Access the internal security admin tool.
    
3.  Reset login credentials.
    
4.  Confirm password requirements.
    
5.  Enable / verify 2FA.
    
6.  Test login with customer.
    
7.  Document the incident internally.
    

### **Reg E Unauthorized ATM Withdrawal**

**Prompt:**_Walk me through the internal Reg E dispute steps for an unauthorized ATM withdrawal._

**Model Response (excerpt):**

1.  Collect transaction details & customer statement.
    
2.  Create a Reg E case.
    
3.  Notify customer of timeline (10 days provisional, 45 days investigation).
    
4.  Block affected card.
    
5.  Review account for prior issues.
    
6.  File police report if applicable.
    
7.  Document all findings.
    
8.  Follow up as necessary.
    

**6\. File Structure**
----------------------

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   retail_banking_internal_agent_fine_tune/  │  ├── logs/  │   ├── run.json  │   ├── training_metrics.json  │   ├── stdout-summary.txt  │  └── README_fine_tune.md   `

**7\. How to Reproduce**
------------------------

High-level reproduction steps:

1.  Create an Azure AI Foundry project.
    
2.  Prepare a JSONL dataset of internal-style Q&A examples.
    
3.  Upload dataset to **Fine-Tuning** section.
    
4.  Configure:
    
    *   gpt-4o-mini-2024-07-18
        
    *   batch size 2
        
    *   LR multiplier 1
        
    *   epochs 3
        
5.  Run job and monitor loss & accuracy curves.
    
6.  Deploy the resulting fine-tuned model.
    
7.  Test in Azure (Playground or REST API).
    

**8\. Intended Use**
--------------------

This repository is intended for:

*   **Portfolio demonstration** of Azure OpenAI fine-tuning
    
*   **Showcasing experience** with dataset creation, model training, deployment
    
*   **Serving as a template** for future domain-specific fine-tuning projects
    

The dataset is **synthetic and generalized**, and not tied to any real bank or proprietary internal system.
