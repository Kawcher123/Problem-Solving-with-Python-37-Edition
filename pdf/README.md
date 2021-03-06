## To build LaTeX --> .pdf

cd into the conversion_tools directory. Run the main script in nb2latex.py

```
$ conda activate book37
(book37)$ cd conversion_tools
(book37)$ python nb2latex.py
```

open ```/pdf/out.tex``` in TexWorks. Put a ```*``` by the Preface chapter header and the Appendix chapter header. Follow with a line to add the chapter back to the table of contents.

```
\chapter*{Preface}\label{preface}
	\addcontentsline{toc}{chapter}{Preface}
```

Also do this with the sections of the preface. So the first section needs to be changed to

```
 \section*{Motivation}\label{motivation}
        \addcontentsline{toc}{section}{Motivation}
```

 Typeset with XeLaTeX twice to produce .pdf

 Note: to make a section double column (really to make the section be surrounded by the ```\begin{problems}``` and  ```\end{problems}```): View the cell metadata, and inside the metadata include the JSON:

 ```
 {
  "latex": {
    "environment": "problems"
  }
}
```

Add in the Copywrite Page and Dedication Page between ```\maketitle``` and ```\tableofcontents```

```
    \maketitle
    
    \input{copywrite_page.tex}
    \newpage
    \input{dedication_page.tex}
    \newpage
    
    \tableofcontents
```

Make the table of contents list Appendix sections in letters. Un-number the appendix section in table of contents, then add the \Alpha as the numbering method.

```
\chapter*{Appendix}\label{appendix}
\addcontentsline{toc}{chapter}{Appendix}


\renewcommand{\thesection}{\Alph{section}.}
\setcounter{section}{0}
```

In the Jupyter notebooks chapter in the markdown section, below the ordered list \lstlisting, revise to:

```
produces

\begin{enumerate}
\item First item
\item Second item
\item Third item
\begin{enumerate}
\item sub item
\item sub item 
\begin{enumerate}
  \item sub-sub item
  \item sub-sub item
\end{enumerate}
\end{enumerate}
```

For the html super-script part of the Jupyter notebook markdown interface, change to:

```
\begin{lstlisting}
x<sup>2</sup>
\end{lstlisting}

produces

x\textsuperscript{2}
```

For the color text part of the Jupyter notebook markdown interface, change to:

```
\begin{lstlisting}
<font color=red>Red Text</font>
\end{lstlisting}

produces

\textcolor{red}{Red Text}
```

In NumPy chapter the np.logspace() error return is longer than one line. Replace in LaTeX with:

```
    \begin{Verbatim}[commandchars=\\\{\}]
RuntimeWarning: overflow encountered in power
  return \_nx.power(base, y)
    \end{Verbatim}
```
