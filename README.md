# il-plus
#### Pieni skripti iltalehden plus -artikkeleiden lukemiseen. Skripti perustuu sivun mukana ladattavaan jsoniin, jossa on plus-artikkeli kokonaisuudessaan vaikka ei olisi maksava asiakas. Tämä skripti vain renderöi renderöimättä jätetyn jsonin artikkelin muotoon.

## Bookmarklet:
#### Käyttö: kopioi koko rivi bookmarkin urlin tilalle ja tallenna sille haluamasi nimi. Kun selaat iltalehden plus-artikkeleita, voit avata bookmarkin (bookmarkletin) jolloin se ajaa javascript-koodin ja renderöi edellämainitun jsonin.\
https://www.freecodecamp.org/news/what-are-bookmarklets/
```
javascript:(()=>{let doc=document.getElementsByClassName("article-body")[0];doc.innerHTML="";doc.style.cssText="padding:20px;font-size:18px;";Object.values(window.App.state.articles)[0].items.body.map((a)=>{let dive=document.createElement("div");try{dive.innerText=a.items.map((b)=>{return b.text?b.text:b.items[0].text;})+"\n\n";}catch(e){if(a.type=="subheadline"){dive=document.createElement("H3");dive.innerText=a.text+"\n";}else if(a.type=="image"){dive=document.createElement("img");dive.src=a.urls.default;}}try{doc.appendChild(dive);}catch(e){};});})();
```


## Siistimpi versio developer consoleen pastettavaksi:
```
let doc = document.getElementsByClassName("article-body")[0];
  doc.innerHTML = "";
  doc.style.cssText = "padding:20px;font-size:18px;";
  Object.values(window.App.state.articles)[0].items.body.map((a) => {
    let dive = document.createElement("div");
    try {
      dive.innerText = a.items.map((b) => {
        return b.text ? b.text : b.items[0].text;
      });
    } catch (e) {
      if (a.type == "subheadline") {
        dive = document.createElement("H3");
        dive.innerText = a.text;
      } else if (a.type == "image") {
        dive = document.createElement("img");
        dive.src = a.urls.default;
      }
    }
    try{
      doc.appendChild(dive);
    } catch(e){};
  });
```

### Troubleshoot:
Q: Skripti ei toimi! Iham paskaa1!\
A: Päivitä sivu kun olet avannut artikkelin. Joskus json ei lataudu ensimmäisellä avauksella.

Q: Edellisen artikkelin tekstit tuli tähän vaikka avasin uuden artikkelin?! Iham paskaa1!\
A: Päivitä sivu ja kokeile uudelleen.

Q: Kokeilin edellisiä ohjeita eikä toimi vieläkään... Iham paskaa1!\
A: Iltalehti lienee korjannut virheensä ja piilottanut artikkelin maksumuurin taakse. Olisit kokeillut aiemmin!

## In English:
Paste either of the scripts to browser developer console and enjoy clickbait articles of il.fi
