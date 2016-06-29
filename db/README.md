# Zakładam że te dane będą wykorzystane też w innych miejscach żeby ich nie duplikować, tabele poprostu się rozrosną z czasem, do większych wersji

## table: client
* client: xxxx

## table: client_domain
* client: xxx
* domain: xxx

## table: client_nap
* client: xxx
* company_name: xxx
* company_brand_names: xxx
* address: xxx
* zip: xxx
* city: xxx
* state: xxx
* phone: xxx
* email: xxx

## table: client_social
* client: xxx
* social_domain: xxx
* social_client_url: xxx

## table: client_domain_url:
* client: xxx
* domain: xxx
* domain_url: xxx
* main_keyword: xxx
* other_keywords: xxx

## table: client_txt:
* client: xxx
* domain_url: xxx
* txt_type: xxx
* txt_title: xxx
* txt_body: xxx

## table: client_login:
* client: xxx
* login: xxx
* email: xxx
* password: xxx

## table: client_report:
* client: xxx
* url: xxx

## table: action
* client: xxx
* site: xxx
* action: xxx

## table: action_steps
* site: xxx
### KEYS
* key_site - strona której to dotyczy
* key_action - akcja jakiej to dotyczy - taką samą nazwę dostaje zmienna w JS
* status - czy pole jest aktywne czy nie
* value - wartość do użycia lub podstawienia

### REGEXP
* regexp - treść regexpa- w () to co ma wyciągnąć do {{!EXTRACT}} można wstawić value - zostanie podmienione wartością z pola value
* regexp_true - kiedy wartosć jest prawdą
* regexp_false - kiedy wartość jest fałszem
* regexp_desc - opis co regexp wyciąga

### TAG, EVENT, EVENTS
* tag - TAG, EVENT, EVENTS, FRAME
* tag_pos - POS=%s
* tag_num - F=%s
* tag_name - NAME=%s
* tag_field -  TYPE=INPUT, SUBMIT + :
* tag_field_type - TYPE=TEXT, KEYPRESS itp.
* tag_form - FORM=%s
* tag_attr_type - ATTR=ID:
* tag_attr - ATTR=ID:id_name
* tag_content = CONTENT=%s
* tag_selector_element - SELECTOR=#
* tag_selector - SELECTOR=#selector
* button_point_char_key - BUTTON, POINT, CHAR, CHARS
* button_point_char_key_val - CHARS=%s
* Spacje zastępuje <SP>

### JS
* js - nazwa funkcji
* js_before_after - czy ma wystąpić przed czy po danym polu
* js_atr1 - atr 1
* js_atr2 - atr 2
*  - ustawia tylko wartość

### FUNKCJE OBSŁUGIWANE JEDNYM POLEM, WARTOŚCIĄ
* func_url_goto
* func_extract_popup
* func_encryption
* func_error
* func_wait_sec
* func_timeout
* func_tab
* func_clear
* func_refresh


## Akcja:
* init - inicjalizacja skryptu
* register - rejestracja w serwisie
* login - logowanie do serwisu
* addblog - dodawanie nowego bloga + otrzymanie adresu do tego bloga, dodatkowy krok oprócz rejestracji.
* addpost - dodawanie posta/wpisu
* GoTo - akcja szczegółowa, idź gdzieś przejdź gdzieś żeby tam wykonać akcje
* Form - jak już tam jesteś wypełnij ten formularz
* Check - sprawdź czy zrobiłeś prawidłowo to co miałeś zrobić

