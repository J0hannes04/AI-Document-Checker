# Bild2JSON-Pipeline – SAP Screenshot Extraction

Dieses Repository enthält die vollständige Implementierung einer Bild2JSON‑Pipeline,
die SAP‑Screenshots mithilfe eines multimodalen Large Language Models (Qwen2.5 VL 7B Instruct)
in strukturierte JSON‑Repräsentationen überführt.  
Die Pipeline wurde im Rahmen einer Projektarbeit an der TH Mittelhessen entwickelt.

Ziel der Pipeline ist es, **variable Inhalte** aus SAP‑Oberflächen automatisch zu extrahieren
und in **vergleichbare JSON‑Strukturen** zu überführen.  
Statische UI‑Elemente werden bewusst ignoriert, um ausschließlich die relevanten Unterschiede
zwischen mehreren Abgaben derselben Aufgabe sichtbar zu machen.

Unterstützte Klassen:

- **Excel** – tabellarische SAP‑Listen  
- **DTP** – Data Transfer Process Oberflächen  
- **Transformationen** – Mapping‑Tabellen zwischen Quelle und Ziel  

Jede Klasse besitzt ein eigenes JSON‑Schema und einen eigenen Prompt.


Die Pipeline kombiniert zwei Modelle:

1. **ResNet‑18**  
   - Klassifiziert den Screenshot in eine der drei Klassen  
   - Steuert das Prompt‑Routing

2. **Qwen2.5 VL 7B Instruct**  
   - Multimodales LLM  
   - Extrahiert Inhalte basierend auf dem klassenspezifischen Prompt  
   - Gibt ausschließlich gültiges JSON zurück

Die Pipeline wurde auf dem THM JupyterLab‑Server ausgeführt.  
Benötigte Python‑Bibliotheken:

- `transformers`
- `accelerate`
- `torch`
- `torchvision`
- `bitsandbytes`
- `pillow`

Installation:

```bash
pip install transformers accelerate torch torchvision bitsandbytes pillow

Für den Zugriff auf das Qwen‑Modell ist ein Hugging‑Face‑Token erforderlich:

huggingface-cli login

Eigene Testdaten erforderlich
Dieses Repository enthält keine Beispielbilder.
Um die Pipeline auszuführen, müssen Nutzer eigene SAP‑Screenshots bereitstellen.



