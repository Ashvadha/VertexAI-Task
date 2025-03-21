Founder-Investor Matching – Approach Summary
This project implements a Python-based solution to match startup founders with potential investors based on shared industry interests, preferred funding stages, and cheque size compatibility. The goal is to create an efficient and scalable matching system to help founders connect with suitable investors.

✅ Objective
The objective of this project is to create a program that:

Takes a founder's profile as input
Matches the founder with potential investors based on predefined criteria
Returns a list of suitable investors
💡 Approach
1. Data Handling
Founder data is provided as a list of dictionaries, where each dictionary contains the founder's:
Name – Name of the founder
Industry – Industry the startup operates in
Stage – Current stage of the startup (e.g., Seed, Series A)
Funding_Required – Amount of funding required in the format $500K
Investor data is stored in a pandas DataFrame with the following fields:
Investor_Name – Name of the investor
Industry – List of industries the investor is interested in
Stage – List of startup stages the investor invests in
Cheque_range – Range of funding the investor is willing to provide
2. Matching Logic
The matching logic consists of three main filters:

➡️ Industry Match
Check if the founder's industry matches any industry listed in the investor's profile.
Convert industry names to lowercase to handle case insensitivity.

➡️ Stage Match
Check if the founder’s stage matches any stage listed in the investor's profile.
Use list comparison to handle multiple stages.

➡️ Funding Match
Extract the minimum and maximum cheque range from the investor’s profile.
Convert the founder's funding requirement to a numeric value.
Check if the funding amount falls within the specified range.
3. Implementation
The match_founders_with_investors function takes two inputs:

A single founder's profile
The investor DataFrame
The function applies the matching logic in the following order:
✅ Industry match → ✅ Stage match → ✅ Funding match

Suitable matches are collected and printed in a structured format.

The task_1.ipynb has the code. investor_matches.json is a sample output for one particular founder profile.
