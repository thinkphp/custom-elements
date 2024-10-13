# custom-elements

One of the key features of web components is the ability to create custom elements: that is, HTML elements whose behavior is defined by the web developer, that extend the set of elements available in the browser.


# Introducere la Shadow DOM și Shadow Root

Shadow DOM este o caracteristică puternică a platformei web moderne care permite încapsularea structurii, stilului și comportamentului într-un sub-arbore DOM separat. Această tehnologie este crucială pentru crearea de componente web reutilizabile și izolate.

## Ce este Shadow DOM?

Shadow DOM permite browserului să randeze un sub-arbore DOM separat de DOM-ul principal al documentului. Acest sub-arbore este cunoscut sub numele de "shadow tree", iar punctul de atașare la DOM-ul principal se numește "shadow root".

## Shadow Root

Shadow Root este punctul de început al Shadow DOM. Este un obiect special care se atașează la un element normal din DOM-ul principal, cunoscut sub numele de "shadow host". Orice conținut în interiorul Shadow Root este izolat de restul paginii.

## Avantajele utilizării Shadow DOM:

1. **Izolare CSS**: Stilurile definite în interiorul Shadow DOM sunt limitate la acel shadow tree și nu afectează restul paginii.

2. **Încapsulare**: Elementele din interiorul Shadow DOM nu sunt accesibile direct din DOM-ul principal, oferind o separare clară a responsabilităților.

3. **Simplificarea marcajului**: Permite crearea de componente complexe cu un marcaj extern simplu.

4. **Evitarea conflictelor**: Reduce șansele de conflicte de nume de clase sau ID-uri între diferite părți ale aplicației.

## Cum se creează un Shadow Root

Iată un exemplu simplu de creare a unui Shadow Root:

```javascript
// Selectăm un element care va fi gazda Shadow DOM-ului
const host = document.querySelector('#host');

// Creăm un Shadow Root
const shadowRoot = host.attachShadow({mode: 'open'});

// Adăugăm conținut în Shadow DOM
shadowRoot.innerHTML = `
  <style>
    p { color: red; }
  </style>
  <p>Acest paragraf este în interiorul Shadow DOM</p>
`;
```

În acest exemplu, `mode: 'open'` permite accesul la Shadow DOM din exterior prin proprietatea `element.shadowRoot`. Dacă folosim `mode: 'closed'`, Shadow DOM-ul nu va fi accesibil din exterior.

## Utilizări comune

Shadow DOM este folosit frecvent în:
- Crearea de componente web personalizate
- Încapsularea logicii și stilului widget-urilor
- Construirea de interfețe utilizator modulare și reutilizabile

Înțelegerea și utilizarea Shadow DOM și Shadow Root poate îmbunătăți semnificativ modul în care construim și organizăm aplicațiile web moderne.

### References:
https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_custom_elements
