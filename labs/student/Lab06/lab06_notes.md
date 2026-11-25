# Lab 06 notes

Name: Artur Ziółkowski

## Class

Command used to execute the script: python scene_report.py

Two report rows I checked against the rules: D is ELIGIBLE because equality with the limit is allowed, F is INVALID, not CLOUDY, because the invalid check comes first.

Observed counts at a limit of 20: ELIGIBLE 5, CLOUDY 1, INVALID 2

My explanation of one loop, return, or repeated record decision: Both records labeled A belong in the result because each row is a separate record, the report keeps every input row in order, and a scene_id is just a label, not a unique key. Also, return results sits after the loop so the function returns the full list, not just after the first scene.

Agreed stopping point, if setup or time prevented completion:

## At home

Predicted selected labels and sizes at an individual limit of 250 MB, before running: H1 250, H3 150, H1 100. H2 800 and H7 450 are eligible by cloud but exceed 250 MB, H4 is CLOUDY, H5 is INVALID, H6 is INVALID.

Observed saved rows, and any explanation of a mismatch: H1 250, H3 150, H1 100

Prediction and observed result at 100 MB: 
I predicted only the second H1 would remain. Observed one row - H1 100. The 150 MB H3 and the 250 MB H1 were dropped for being over 100 MB, while the 100 MB H1 stayed because it equals the limit.

One suggestion I accepted or changed and the example that checked it, or my own check if I used no LLM:
I used Claude for the loop in choose_scenes. I accepted calling assess_scene and then checking ELIGIBLE and size_mb <= max_size_mb. The exact example that checked <= was the first H1 (cloud 20, size 250), which is exactly at both limits and was kept at 250 MB. At 100 MB the second H1 (size 100) was kept.