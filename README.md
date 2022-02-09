# Tembo Notes

<img
    src="https://github.com/tembo-core/tembo-notes/blob/develop/assets/tembo_notes_banner.png?raw=true"
    width="750px"
/>

A simple folder organiser for your work notes.

![GitHub Workflow Status](https://img.shields.io/github/workflow/status/tembo-core/tembo-notes/analysis?style=flat-square)
![Sonar Tests](https://img.shields.io/sonar/tests/tembo-core_tembo-notes?compact_message&failed_label=failed&passed_label=passed&server=https%3A%2F%2Fsonarcloud.io&skipped_label=skipped&style=flat-square)
![Sonar Coverage](https://img.shields.io/sonar/coverage/tembo-core_tembo-notes?server=https%3A%2F%2Fsonarcloud.io&style=flat-square)
![PyPI](https://img.shields.io/pypi/v/tembo?style=flat-square)
![PyPI - Python Version](https://img.shields.io/pypi/pyversions/tembo?style=flat-square)

Read the documentation here: <https://tembo-core.github.io/tembo-notes/>.
## config.yml

```yaml
# time tokens: https://strftime.org
tembo:
  base_path: ~/tembo
  # template_path: ~/tembo/templates
  scopes:
    - name: scratchpad
      example: tembo new scratchpad
      path: "scratchpad/{d:%B_%Y}"
      filename: "{d:%B_%W}"
      extension: md
      template_filename: scratchpad.md.tpl
    - name: wtodo
      example: tembo new wtodo | directory is month_year, filename is month_week-of-year
      path: "wtodo/{d:%B_%Y}"
      filename: "week_{d:%W}"
      extension: todo
      template_filename: weekly.todo.tpl
    - name: meeting
      example: tembo new meeting $meeting_title
      path: "meetings/{d:%B_%y}"
      filename: "{d:%a_%d_%m_%y}-{input0}"
      extension: md
      template_filename: meeting.md.tpl
    - name: knowledge
      example: tembo new knowledge $project $filename
      path: "knowledge/{input0}"
      filename: "{input1}"
      extension: md
      template_filename: knowledge.md.tpl
  logging:
    level: INFO
    path: ~/tembo/.logs
```

## templates

###  knowledge

```
---
created: {d:%d-%m-%Y}
---

# {input0} - {input1}.md
```

### meeting

```
---
created: {d:%d-%m-%Y}
---

# {d:%A %d %B %Y} - {input0}

## People

Head:

Attendees:

## Actions


## Notes

```

### scratchpad

```
---
created: {d:%d-%m-%Y}
---

# Scratchpad - Week {d:%W} - {d:%B-%y}
```

### wtodo

```
---
created: {d:%d-%m-%Y}
---

Weekly TODO | Week {d:%W} {d:%B}-{d:%Y}

Work:

Documentation:
```
