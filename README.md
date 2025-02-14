# GEN-AI-app--ai-code-reviewer
import streamlit as st

# Title of the application
st.title('GenAI App - AI Code Reviewer')

# Text input area for Python code
user_code = st.text_area("Enter your Python code:", height=300)

# Submit button to trigger code review
if st.button('Review Code'):
    if user_code:
        st.write("Code Review in Progress...")
        # Function to process the code review
        review_code(user_code)
    else:
        st.error("Please enter your Python code for review.")


import openai

# OpenAI API Key (make sure to keep this secure)
openai.api_key = "your_openai_api_key"

def review_code(user_code):
    # Make an API call to OpenAI's GPT model
    response = openai.Completion.create(
        engine="code-davinci-002",  # Use the most appropriate model for code review
        prompt=f"Please review the following Python code for bugs, errors, or improvements:\n{user_code}\nProvide feedback and suggest fixes if necessary.",
        max_tokens=150,
        temperature=0.3
    )
    
    review = response.choices[0].text.strip()
    # Display the review result
    st.write("**Code Review Result:**")
    st.write(review)
    
    
    st.write("**Suggested Fixes:**")
    st.code(review)

import openai
import streamlit as st

# OpenAI API key
openai.api_key = "your_openai_api_key"

# Title
st.title('GenAI App - AI Code Reviewer')

# Text input for Python code
user_code = st.text_area("Enter your Python code:", height=300)

# Function to review the code using OpenAI
def review_code(user_code):
    response = openai.Completion.create(
        engine="code-davinci-002",  # Choose the best engine for code review
        prompt=f"Please review the following Python code for bugs, errors, or improvements:\n{user_code}\nProvide feedback and suggest fixes if necessary.",
        max_tokens=150,
        temperature=0.3
    )
    
    review = response.choices[0].text.strip()
    
    # Display the review and suggested fixes
    st.write("**Code Review Result:**")
    st.write(review)
    st.write("**Suggested Fixes:**")
    st.code(review)

# Submit button for code review
if st.button('Review Code'):
    if user_code:
        st.write("Code Review in Progress...")
        review_code(user_code)
    else:
        st.error("Please enter your Python code for review.")
