# Howdy, y'all. Data Mappin' Practice with DADATA

This here's a little project from my systems analysis studies where I had to wrangle some address data and make sure two systems could talk to each other without gettin' their wires crossed.

**The Problem:**
We got an online store (the receiver) expectin' address fields in one format, and a fancy address verification service called DADATA (the source) spittin' out data in another. The goal? Build a mappin' table so the frontend can use DADATA without the backend havin' to change its ways. That's just good, clean livin'.

**What's Inside:**
- **`solution.md`**: The actual mappin' table and the logic for handlin' edge cases (like when the address includes a district or when DADATA just ain't cooperatin').
- **`json-examples/`**: A couple of JSON payloads showin' how the final order object looks when the address checks out... and when it don't.

**Skills Practiced:**
- Requirements Analysis
- Data Mapping & Integration Logic
- JSON Structure Design
- Edge Case Handling (because the real world is messy)

This ain't the fanciest project, but it shows I can take a requirement, break it down, and document it so a developer could run with it. Fixin' to add more like this as I go.

**Why This Matters for a Systems Analyst:**
If you can't describe how data gets from point A to point B without turnin' into a train wreck, you're just guessin'. Mappin' exercises like this build the muscle memory for writin' clear specs and handlin' errors gracefully.
