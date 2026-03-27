# CGM Sensor Integrity Detector

*An analytic for identifying locally unreliable CGM traces*

**Author:** Dan Heller
**Published:** 2026
**License:** © 2025–2026 Dan Heller. MIT License — https://github.com/argv01/cgm-sensor-integrity/blob/main/LICENSE

This package accompanies the Substack article *The CGM Patent That Can Save Lives*:
https://danheller.substack.com/p/the-cgm-patent-that-could-save-lives

The article explains how CGM sensor noise can be misinterpreted as valid glucose readings, which can then affect dosing decisions, either by a human or AID algorithms. These can be potentially dangerous if the noise is bad enough and lasts long enough, particularly at night for AID system users, where a potentially harmful amount of insulin could be infused.

The article then explains how I developed an algorithm to detect these clusters of unreliable glucose readings. This package contains that algorithm, a report renderer, sample CGM datasets, and an API layer for programmers to interrogate their own large datasets from other sources. See the API directory for details.

Naturally, users can use this detector to analyze their own CGM data.

The code is written in Python, and you're certainly welcome to read it and use it on your local computer using command-line tools to analyze your own data. But unless you're a programmer and wish to get into the bowels of the code and make edits, that's going to be a waste of time.

The best way to do that is to download **`cgm_ai_assistant.zip`** from the [releases page](https://github.com/argv01/cgm-sensor-integrity/releases) and upload it to an AI assistant (Claude, ChatGPT, Gemini, etc.) along with your CGM data that you downloaded from the portal associated with your CGM. For Dexcom, use [clarity.dexcom.com](http://clarity.dexcom.com), login, change the number of days you want to analyze to 90 (for a full report), and choose "Export" — do not use "Download", because that will produce a PDF that's not useful here. You want a CSV file or an xlsx workbook file. (Sugarmate allows you to send you a report in this format as well.) For Tandem pump users, you can export directly from [source.tandemdiabetes.com](https://source.tandemdiabetes.com) — this gives you CGM *and* insulin delivery data in one file, which the tool will render together on the same chart. For Abbott Libre, export from [libreview.com](https://libreview.com).

Once you upload that file and `cgm_ai_assistant.zip` to your AI assistant, you can have it produce a full report, or produce daily graphs, whatever.

You can aggregate large amounts of data as well, including periods where you changed CGM models or brands, comparing the two. Multi-sensor analysis will be done automatically if multiple sensor types are detected in the data.

**A note on AI compatibility:** Results vary depending on which AI assistant you use and how it's configured. This package includes a Bootstrap Contract — a set of instructions the AI reads before doing anything — but not all AI environments support running Python scripts or returning image files to the user. Claude (claude.ai) works best and is the recommended platform. Gemini Advanced can run scripts but may hit memory or time limits on large datasets. Free-tier Gemini, ChatGPT, and institutional deployments may not be able to execute scripts at all — in those cases the AI should tell you so and offer to walk you through running it locally.

If things don't go as expected, try: uploading again in a fresh session, asking the AI explicitly to "run cgm_render_report_v6.py on my file and show me the dashboard PNG", or trying a different AI assistant. If you get a text summary instead of an image, the AI was unable to run the scripts — that's a limitation of the environment, not the package.

See `main/README.md` for a full list of example prompts.

---

**First-time setup:** `pip install -r requirements.txt`

## Downloads

All files are on the [releases page](https://github.com/argv01/cgm-sensor-integrity/releases):

| File | Who it's for |
|------|--------------|
| `cgm_ai_assistant.zip` | Most users — upload to an AI assistant |
| `cgm_renders.zip` | Sample PNG reports — see what the output looks like |
| `cgm_sample_scripts.zip` | Programmers running locally |
| `cgm_api.zip` | Developers with large population datasets |

`cgm_sample_scripts.zip` and `cgm_api.zip` require the core files from `cgm_ai_assistant.zip` extracted into the same folder.
