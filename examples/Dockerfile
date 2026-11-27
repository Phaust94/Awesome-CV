# Use a lightweight but complete TeX Live distribution
FROM texlive/texlive:latest@sha256:aded8a18d311f923dd89a4cd76450e9b81dfe0a6e74d191bd3efd9af1c8dbe4c

# Set the working directory inside the container
WORKDIR /resume

# Copy everything from your local directory into the container
# This includes your main.tex, support files, and fonts
COPY fonts /resume/fonts

# 1. Register fonts (LuaLaTeX can find fonts in the current dir,
# but registering them with the system is safer)
RUN mkdir -p /usr/share/fonts/truetype/custom && \
    find . -name "*.ttf" -o -name "*.otf" -exec cp {} /usr/share/fonts/truetype/custom/ \; && \
    fc-cache -f -v

COPY . .

# 2. Compile using LuaLaTeX
# -pdflua: Tells latexmk to use lualatex
# -interaction=nonstopmode: Don't pause on errors
# -output-directory=out: Keeps your project root clean
RUN mkdir -p out && \
    latexmk -pdflua -interaction=nonstopmode -output-directory=out resume.tex

CMD ["sleep", "infinity"]