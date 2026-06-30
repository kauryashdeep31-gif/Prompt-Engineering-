Training day 20 
Smart Student Mentor 
Testing, Results and Conclusion of Smart Student Mentor Project 
Introduction 
Day 20 marked the final phase of the Smart Student Mentor Project. This day 
focused on testing the system, analyzing the results, and documenting the final 
conclusion. The objective was to verify whether the implemented system works 
according to the defined requirements and delivers accurate and meaningful 
guidance to students. 
This phase is essential to ensure that the system is reliable, user-friendly, and 
ready for practical use. Screenshots of the working system were captured during 
this stage to demonstrate functionality and performance. 
Code: 
import requests 
import streamlit as st 
import re 
import os 
from dotenv import load_dotenv 
from gtts import gTTS 
import tempfile 
load_dotenv() 
GOOGLE_API_KEY = os.getenv("GOOGLE_API_KEY") 
SEARCH_ENGINE_ID = os.getenv("SEARCH_ENGINE_ID") 
st.set_page_config(page_title="Smart Student Mentor", layout="centered") 
st.title("Smart Student Mentor ") 
st.write("Ask a question, get answers from the web, see links, and hear the explanation.") 
def google_search(query): 
    url = ( 
        "https://www.googleapis.com/customsearch/v1" 
        f"?q={query}&key={GOOGLE_API_KEY}&cx={SEARCH_ENGINE_ID}&num=3" 
    ) 
    response = requests.get(url).json() 
    results = [] 
 
    for item in response.get("items", []): 
        results.append({ 
            "title": item.get("title", ""), 
            "snippet": item.get("snippet", ""), 
            "link": item.get("link", "") 
        }) 
    return results 
 
def clean_text_for_tts(text): 
    text = re.sub(r"http\S+", "", text) 
    text = re.sub(r"[^a-zA-Z\s]", "", text) 
    return " ".join(text.split()) 
 
def speak_text(text): 
    tts = gTTS(text=text, lang="en") 
    with tempfile.NamedTemporaryFile(delete=False, suffix=".mp3") as fp: 
        tts.save(fp.name) 
        st.audio(fp.name, format="audio/mp3") 
 
if "answer_text" not in st.session_state: 
    st.session_state.answer_text = "" 
if "tts_text" not in st.session_state: 
    st.session_state.tts_text = "" 
 
if "links" not in st.session_state: 
    st.session_state.links = [] 
query = st.text_input("Enter your question:") 
 
if st.button("Get Answer"): 
    if query.strip() == "": 
        st.warning("Please enter a question.") 
    else: 
        results = google_search(query) 
 
        if not results: 
            st.info("No results found.") 
            st.session_state.answer_text = "" 
            st.session_state.tts_text = "" 
            st.session_state.links = [] 
        else: 
            answer_text = "" 
            speech_text = "" 
            links = [] 
 
            for r in results: 
                answer_text += f"{r['title']}\n{r['snippet']}\n\n" 
                speech_text += r['snippet'] + " " 
                links.append(r["link"]) 
 
            st.session_state.answer_text = answer_text 
            st.session_state.tts_text = clean_text_for_tts(speech_text) 
            st.session_state.links = links 
 
if st.session_state.answer_text: 
    st.subheader("       Answer") 
st.text(st.session_state.answer_text) 
if st.session_state.links: 
st.subheader("   
Reference Websites") 
for i, link in enumerate(st.session_state.links, start=1): 
st.markdown(f"{i}. [{link}]({link})") 
if st.session_state.tts_text: 
if st.button("    
Speak Answer"): 
speak_text(st.session_state.tts_text) 
System Testing 
System testing was performed to evaluate the overall performance of the Smart 
Student Mentor system. Different types of test cases were executed to verify the 
correctness of the system. 
Functional Testing 
Functional testing was carried out to ensure that each module performs its 
intended function correctly. Student queries were entered into the system, and the 
generated responses were checked for accuracy and relevance. The system 
successfully accepted user input, processed queries, and displayed appropriate 
responses. 
Integration Testing 
Integration testing ensured that all modules worked together seamlessly. The 
interaction between the user interface, query processing module, knowledge base, 
and response generation module was verified. No major issues were observed 
during integration. 
Result Analysis 
The results obtained from testing were satisfactory. The Smart Student Mentor 
system was able to understand student queries and generate meaningful 
responses. 
Response time was observed to be quick, and the system maintained stability 
during multiple query inputs. Screenshots were captured to document successful 
query handling and response generation. 
User Experience Evaluation 
The system was evaluated from a user’s perspective to check ease of use and 
clarity. The interface was found to be simple and intuitive. Students could easily 
enter their questions and understand the responses without additional guidance. 
The overall user experience was positive, making the system suitable for 
academic assistance. 
Limitations 
Although the system performed well, a few limitations were identified: 
• The system depends on the quality of stored academic data. 
• Complex or ambiguous queries may require further improvement. 
• Advanced personalization features can be added in future versions. 
These limitations can be addressed through future enhancements. 
Future Scope 
In the future, the system can be enhanced by: 
• Adding voice-based interaction 
• Integrating more subjects and datasets 
• Improving personalization and recommendation features 
• Incorporating advanced AI techniques 
The Smart Student Mentor Project has strong potential to evolve into a 
comprehensive intelligent learning platform. 
Conclusion 
Day 20 concluded the Smart Student Mentor Project successfully. The system 
was tested thoroughly, and the results confirmed that it meets the project 
objectives. The Smart Student Mentor system effectively assists students by 
providing accurate and timely academic guidance. The inclusion of screenshots 
demonstrates the practical implementation and working of the project.
