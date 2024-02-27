start venv py -3.11 -m venv .venv
active venv .venv\Scripts\activate
install flask pip install Flask
RUN flask --app FILENAME run
export deps pip freeze > packages.txt
install deps pip install -r packages.txt

pywin32 package only works for windows so when dockersing you need to add => ;sys_platform == 'win32' to the end of it

