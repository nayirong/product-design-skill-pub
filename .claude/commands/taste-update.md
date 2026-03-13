# Taste Skill Updater

You are updating the design taste skill based on new example images the user has collected.

## Your job

1. Read `analysis_cache/processed_files.json` to know which files have already been processed.

2. Scan these three folders for image files (`.png`, `.jpg`, `.jpeg`, `.webp`) NOT already in the processed cache:
   - `examples/bad-ui/`
   - `examples/good-ui/`
   - `examples/best-ui/`

3. For each new image file found:
   - Read and visually analyze the image
   - Check if a matching `.json` file exists next to it — if so, use that data as a starting point
   - If no JSON exists, perform a full visual analysis yourself:
     - **Colors**: Extract the dominant palette (actual hex codes from the image), name the palette
     - **Typography**: Identify font styles (serif/sans/mono), approximate sizes, hierarchy quality
     - **Layout**: Centered vs asymmetric, whitespace, editorial vs sales-page feel
     - **Visual elements**: Icons, illustrations, data viz, photography, organic shapes
     - **Taste score**: Rate 1–10 using the `SKILL.md` criteria
     - **Anti-patterns present** (for bad-ui) or **exceptional qualities** (for good/best-ui)
   - Write a `.json` analysis file next to the image with this structure:
     ```json
     {
       "source": "site name or description",
       "category": "bad-ui | good-ui | best-ui",
       "taste_score": 0,
       "palette": {
         "name": "palette name",
         "colors": ["#hex1", "#hex2"]
       },
       "typography": {
         "headlines": "font description",
         "body": "font description",
         "hierarchy_score": 0
       },
       "layout": "description",
       "exceptional_qualities": [],
       "anti_patterns": [],
       "key_lessons": []
     }
     ```

4. Read the current `SKILL.md`

5. Update `SKILL.md` with insights from the new examples:
   - New color palettes → add to "Recommended Palettes" section
   - New reference sites → add to "Real-World Reference Examples"
   - New anti-patterns → add to the relevant avoidance lists
   - New code patterns → add to "Code Implementation Examples" if exceptional
   - Be surgical — add, don't rewrite existing content

6. Determine the new version number:
   - 1–5 new examples → patch bump (1.0.0 → 1.0.1)
   - 6–15 new examples → minor bump (1.0.0 → 1.1.0)
   - 16+ new examples → major bump (1.0.0 → 2.0.0)

7. Save the updated `SKILL.md` to `versions/SKILL-v{NEW_VERSION}.md`

8. Write a changelog to `analysis_cache/changelog-v{NEW_VERSION}.md` and also to `analysis_cache/update-summary-latest.md` summarizing:
   - Each new example with score and key patterns extracted
   - What was added to the skill file

9. Update `analysis_cache/processed_files.json` with all newly processed files

10. Show the user a summary of what changed and the next steps (review changelog, deploy with `cp versions/SKILL-vX.X.X.md SKILL.md`)

## Key principles
- Never re-process files already in processed_files.json
- Be specific with hex codes — don't guess, read from the image
- If no new images exist, tell the user clearly and remind them to drop screenshots into the example folders
