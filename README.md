# web-renderer

### Requests:

```
paths:
    /:
    post:
        summary: Render a document.
        requestBody:
            json_data:
                description: json data of the Tender
                content: application/json:
            template:
                description: template .docx file
                content: file
        responses:
        '200':
            file: Generated file
```

### Jinja template functions:

- ##### `{{ iso_str_date | format_date}}`  
   The function for formating an ISO date to the string one. 
    - **input:** date (ISO): 2019-08-22T13:35:00+03:00 
    - **output:** date (str): "22" серпня 2019 року 
- ##### `{{ str_float_number | to_float}}`
    The function for formatting comma float string to float. 
    - **input:** "12\xa0588\xa0575.00" 
    - **output:** 12588575.0 
- ##### `{{ str_float_number | convert_amount_to_words}}`
    The function for formatting an amount of money to the word string.
    - **input:** "12\xa0588\xa0575.00" 
    - **output:** "триста двадцять двi тисячi шiстсот шiстдесят дев'ять гривень 00 копійок"
- ##### `{{items_list | common_classification }}`
    The function for formatting common classification of all items in format "ДК021 32100000-1, Текстовий опис класифікатора"
    - **input:** "Список айтемів контракту"
    - **output:** "Текстове значення класифікатора у форматі: 'ДК021 32100000-1, Текстовий опис класифікатора'"
- ##### `{{items_list | common_classification_code}}`
    The function for formatting common classification of all items in format "ДК021 32100000-1
    - **input:** "Список айтемів контракту"
    - **output:** "Текстове значення класифікатора у форматі: 'ДК021 32100000-1'"
- ##### `{{items_list | common_classification_description}}`
    The function for getting common classification description of all items
    - **input:** "Список айтемів контракту"
    - **output:** "Текстовий опис спільного для всіх айтемів класифікатора"


### Run tests

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
pytest --cov
```
