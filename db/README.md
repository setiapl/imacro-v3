# DB project
*Zakładam że te dane będą wykorzystane też w innych miejscach żeby ich nie duplikować, tabele poprostu się rozrosną z czasem, do większych wersji*

## Client
* client: xxxx
** klient jest unikalny

## Domeny client
* client: xxx
* domain: xxx
** klient może mieć wiele domen
** domena może być tylko przypisana do jednego klienta

## client_nap
* client: xxx
* company_name: xxx
** nazwa firmy może się zmienić
* company_brand_names: xxx
** nazw brandowych lub skróconych może być wiele
* address: xxx
* zip: xxx
** może się zmienić
* city: xxx
** może się zmienić
* state: xxx
** może się zmienić
* phone: xxx
** może się zmienić
* email: xxx
** może się zmienić

** jeśli adres bądź nazwa się zmieni to chce wiedzieć od kiedy działa nowa  wersja

## client_social
* client: xxx
* social_domain: xxx
** domeny są wspólne i się powtarzają
* social_client_url: xxx
** url jest unikalny dla klienta

## client_domain_url:
* client: xxx
* domain: xxx
* domain_url: xxx
** url jest unikalny
* main_keyword: xxx
** to jest główne słowo kluczowe
* other_keywords: xxx
** inne pasujące słowa kluczowe dodanego URL-a

## client_txt:
* client: xxx
* domain_url: xxx
** do jakiego konkretnego URL-a jest dany tekst
** jeżeli tekst jest dla głównej domeny a dla URL-a nie ma to używamy dla  głównej
* txt_type: xxx
** typ txt np. synonim, uniq, tłumaczony z EN uniq lub synonim
* txt_title: xxx
** tytuł artykułu
* txt_body: xxx
** treść artykułu, może zawierać obrazki, filmy linki

## client_login:
* client: xxx
* site
** serwis do którego te dane używamy
* login: xxx
** login do serwisu x
* email: xxx
** email do serwisu x
* password: xxx
** hasło do serwisu x

## client_report:
* client: xxx
* url: xxx
** link utworzony
* anchor: xxx
** anchor linka utworzonego
* link_type: xxx
** np. txt, img, itp.
* data utworzenia linku

## works
* client: xxx
* site: xxx
** na jakim serwisie wykonujemy akcje
* work: xxx
** jaką akcję wykonujemy

## action
* do wymyślenia
* informacja jakie akcje trzeba wykonać żeby osiągnąć konkretną akcję
* trzba opisać wszystko co ma zrobić i jak ma zrobić

## fields
* site: xxx
** jakiej strony to dotyczy
### KEYS
* action
** jakiej akcji to dotyczy init, login, register itp.
* action_steps
** konkretne kroki np. goto, wypełnienie pola, check
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


END
------------------------------------------
client
request
actions
templates


template- np. logowanie do FB



def getClient(nazwa):
    klient=db.getdict('select * from kient where nazwa = %s',[nazwa])[0]
    res=db.getresult('select nazwa, wartosc from dane_klienta where
    id_klienta = %d',[klient['id']])
    klient['dae']=dict()
    for row in res:
        klient['dane'][row[0]]=row[1]
    return klient


mamy klienta
mamy domeny których może mieć wiele
Domeny są unikalne

def updateClient(id,dane):
