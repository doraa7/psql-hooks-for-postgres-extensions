Short description of this hook.

Remember to mention when it's called, what should it do, what inputs supplied to this hook,
what output is expected and (shortly) how postgres changes its behavior based on received output.

*Inputs:*

{% if hook.type.inputs -%}
Briefly describe hook inputs. Are inputs preprocessed somehow before calling the hook?
Are there any special input states? Can they be null (e.g. `nullptr`)?

{% for input in hook.type.inputs -%}
* <i>{{ input.type }}</i> <b>{{ input.name }}</b> — ...
{% endfor %}
{%- else -%}
There are no inputs for this hook. Is there a global state this hook should introspect?
{%- endif %}
*Output:*

{% if hook.type.output == 'void' -%}
This hook does not produce any output. Describe, what exactly it should do.
Maybe, it should throw an error via a standard `ereport(ERROR, ...)`?
Maybe, there are some mutable inputs this hook should change?
{%- else -%}
Describe hook output. Are there any constraints for the output value?
How postgres changes its behavior based on received output?
Are there any special cases for output, e.g. returning `-1` or `nullptr`?
Are there any mutable inputs this hook should change?
{%- endif %}

*Use-cases:*

It you can think of any use-cases for this hook, spell it out. If no, delete this section.