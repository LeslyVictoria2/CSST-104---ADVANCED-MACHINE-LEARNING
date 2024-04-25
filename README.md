# Link and Compilation of Exercises, Laboratory and Midterm Exam using github.

from bs4 import BeautifulSoup

# Create BeautifulSoup object
html_content = BeautifulSoup(features="html.parser")

# Create the head tag and append title
head_tag = html_content.new_tag("head")
title_tag = html_content.new_tag("title")
title_tag.string = "CSST 104 - Activities and Exercises"
head_tag.append(title_tag)
html_content.append(head_tag)

# Create the style tag and append CSS styles
style_tag = html_content.new_tag("style")
style_tag.string = """
        .btn-container {
            border: 1px solid #ccc;
            padding: 10px;
            width: fit-content;
        }

        .btn-container button {
            display: block;
            background-color: #f1f1f1;
            border: 1px solid #ccc;
            margin-bottom: 5px;
            padding: 10px;
            width: 200px; /* Set a fixed width for the buttons */
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .btn-container button:hover {
            background-color: #ddd;
        }

        .btn-container button.active {
            background-color: #ccc;
        }
"""
html_content.head.append(style_tag)

# Create the body tag and append content
body_tag = html_content.new_tag("body")

# Append the h1 tag
h1_tag = html_content.new_tag("h1")
h1_tag.string = "CSST 104 - Activities and Exercises"
body_tag.append(h1_tag)

# Append the paragraph
p_tag = html_content.new_tag("p")
p_tag.string = "I am Jonathan Q. Laganzon, a BSCS-IS-3B student. This webpage contains my exercises and activities for CSST 104. The activities and exercises focus on building models for regression or prediction, allowing me to explore and apply various concepts in data science and statistical modeling."
body_tag.append(p_tag)

# Append the Activities section
h2_activities_tag = html_content.new_tag("h2")
h2_activities_tag.string = "Activities:"
body_tag.append(h2_activities_tag)

div_activities_tag = html_content.new_tag("div", attrs={"class": "btn-container"})
activities_links = [
    "https://github.com/LeslyVictoria2/CSST-104---ADVANCED-MACHINE-LEARNING/blob/main/3B_VICTORIA_LAB1.ipynb",
]
for i, link in enumerate(activities_links, start=1):
    button_tag = html_content.new_tag("button", onclick=f"window.open('{link}', '_blank')")
    button_tag.string = f"Activity {i}"
    div_activities_tag.append(button_tag)
body_tag.append(div_activities_tag)

# Append the Exercises section
h2_exercises_tag = html_content.new_tag("h2")
h2_exercises_tag.string = "Exercises:"
body_tag.append(h2_exercises_tag)

div_exercises_tag = html_content.new_tag("div", attrs={"class": "btn-container"})
exercises_links = [
    "https://github.com/laganzonj/exercise_activity-CSST104-3B/blob/ef12d6f62645f822e078fd9884b2ee19e68b1575/Exercises/3B-LAGANZON-EXER1.ipynb",
 
]
for i, link in enumerate(exercises_links, start=1):
    button_tag = html_content.new_tag("button", onclick=f"window.open('{link}', '_blank')")
    button_tag.string = f"Exercise {i}"
    div_exercises_tag.append(button_tag)
body_tag.append(div_exercises_tag)

# Append body to HTML content
html_content.append(body_tag)

# Print or save the HTML content
print(html_content.prettify())
