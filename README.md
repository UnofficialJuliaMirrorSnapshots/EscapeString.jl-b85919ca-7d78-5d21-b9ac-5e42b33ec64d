# EscapeString

[![Build Status](https://travis-ci.org/JockLawrie/EscapeString.jl.svg?branch=master)](https://travis-ci.org/JockLawrie/EscapeString.jl)
[![Coverage Status](http://codecov.io/github/JockLawrie/EscapeString.jl/coverage.svg?branch=master)](http://codecov.io/github/JockLawrie/EscapeString.jl?branch=master)


### Usage
EscapeString provides a single function that escapes a given string according to the given format. The function signature is `escapestring(s::AbstractString, fmt::Symbol)`. For example:
```julia
s  = "<div>Hi there 'Sam'!</div>"
s2 = escapestring(s, :html_text)
s2 == "&lt;div&gt;Hi there &#39;Sam&#39;!&lt;/div&gt;"    # true
```

### Available formats
The following formats are currently supported:
- HTML text (`:html_text`)


### Adding new formats
Suppose you would like to add functionality for escaping to XML. To do this:

1. Write a function that takes an `AbstractString` and escapes it to the desired format, say `escape_xml(s::AbstractString)`.
2. Save the function in a file such as `src/escape_xml.jl`.
3. Add `include("escape_xml.jl")` to `src/EscapeString.jl`.
4. Add `formats[:xml] = escape_xml` to `src/EscapeString.jl`.

That's it!


### Todo
1. Other formats will be added over time on an as-needed basis, such as:
    - HTML attribute
    - URL, also known as percent encoding
    - CSS
    - XML
