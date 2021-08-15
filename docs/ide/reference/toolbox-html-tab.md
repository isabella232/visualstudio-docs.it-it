---
title: Casella degli strumenti, Scheda HTML
description: Informazioni sui componenti HTML disponibili nella scheda HTML della finestra Casella degli strumenti.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 672bf1c73aa132cd07f6851256038c56a053359b2131ec224c5387c2289179bc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121232406"
---
# <a name="toolbox-html-tab"></a>Casella degli strumenti, scheda HTML

La scheda **HTML** della casella degli strumenti contiene componenti utili nelle pagine Web e nei Web Form. Per visualizzare questa scheda, aprire un documento per la modifica nella finestra di progettazione HTML. Scegliere **Casella degli strumenti** dal menu **Visualizza** e quindi fare clic sulla scheda **HTML** della casella degli strumenti.

Per creare un'istanza di uno strumento nella scheda **HTML**, fare doppio clic sullo strumento per aggiungerlo al documento nel punto di inserimento corrente o selezionare lo strumento e trascinarlo nella posizione voluta nell'area di modifica.

## <a name="ui-elements"></a>Elementi dell'interfaccia utente

Per impostazione predefinita, nella scheda HTML sono disponibili i seguenti strumenti.

**Puntatore**

![Puntatore pagina HTML di ASP.NET Mobile Designer](../../ide/reference/media/vxpointer.gif)

Questo strumento viene selezionato per impostazione predefinita quando si fa clic su una delle schede della casella degli strumenti e non è possibile eliminarlo. Il puntatore consente di trascinare oggetti nell'area di visualizzazione Progettazione, ridimensionarli e riposizionarli nella pagina o nel form. Per altre informazioni, vedere [Casella degli strumenti](../../ide/reference/toolbox.md).

**Input (Pulsante)**

![Pulsante di pagina Web HTML](../../ide/reference/media/vxbutton.gif)

Consente di inserire un elemento `input` di `type="button"`. Per modificare il testo visualizzato, modificare la proprietà `name`. Per impostazione predefinita, come primo pulsante viene inserito `id="Button1"`, come secondo pulsante `id="Button2"` e così via.

Quando si trascina **Input (Pulsante)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Input (Reimposta)**

![Schermata HTMLpageResetButton](../../ide/reference/media/vxreset.gif)

Consente di inserire un elemento `input` di `type="reset"`. Per modificare il testo visualizzato, modificare la proprietà `name`. Per impostazione predefinita, come primo pulsante di reimpostazione viene inserito `id="Reset1"`, come secondo `id="Reset2"` e così via.

Quando si trascina **Input (Reimposta)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Input (Invia)**

![Schermata HTMLpageToolbarSubmitButton](../../ide/reference/media/vxsubmit.gif)

Consente di inserire un elemento `input` di `type="submit"`. Per modificare il testo visualizzato, modificare la proprietà `name`. Per impostazione predefinita, come primo pulsante di invio viene inserito `id="Submit1"`, come secondo `id="Submit2"` e così via.

Quando si trascina **Input (Invia)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Input (Testo)**

![Schermata HTMLpageToolbarTextField](../../ide/reference/media/vxtextfield.gif)

Consente di inserire un elemento `input` di `type="text"` nel documento. Per modificare il testo predefinito visualizzato, modificare l'attributo `value`. Per impostazione predefinita, come primo campo di testo viene inserito `id="Text1"`, come secondo `id="Text2"` e così via.

Quando si trascina **Input (Testo)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>È consigliabile convalidare tutto l'input degli utenti. Per altre informazioni, vedere [Validating User Input in ASP.NET Web Pages (Razor) Sites](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites) (Convalida dell'input utente nelle pagine Web ASP.NET).

**Input (file)**

![Campo file pagina HTML](../../ide/reference/media/vxfilefield.gif)

Consente di inserire un elemento `input` di `type="file"` nel documento. Per impostazione predefinita, come primo campo file viene inserito `id="File1"`, come secondo `id="File2"` e così via.

Quando si trascina **Input (File)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> È consigliabile convalidare tutto l'input degli utenti. Per altre informazioni, vedere [Validating User Input in ASP.NET Web Pages (Razor) Sites](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites) (Convalida dell'input utente nelle pagine Web ASP.NET).

**Input (Password)**

![Campo della password di Visual Studio](../../ide/reference/media/vxpassword.gif)

Consente di inserire un elemento `input` di `type="password"`. Per impostazione predefinita, come primo campo file password viene inserito `id="Password1"`, come secondo `id="Password2"` e così via.

Quando si trascina **Input (Password)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Se l'applicazione trasmette nomi utente e password, è necessario configurare il sito Web per usare SSL (Secure Sockets Layer) per la crittografia della trasmissione. Per altre informazioni, vedere [Protezione delle connessioni](/previous-versions/tn-archive/bb418917(v=technet.10)). È poi consigliabile convalidare tutto l'input degli utenti. Per altre informazioni, vedere [Validating User Input in ASP.NET Web Pages (Razor) Sites](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites) (Convalida dell'input utente nelle pagine Web ASP.NET).

**Input (Casella di controllo)**

![Opzione della casella di controllo di una pagina Web HTML](../../ide/reference/media/vxcheckbox.gif)

Consente di inserire un elemento `input` di `type="checkbox"`. Per modificare il testo visualizzato, modificare la proprietà `name`. Per impostazione predefinita, come prima casella di controllo viene inserito `id="Checkbox1"`, come seconda `id="Checkbox2"` e così via.

Quando si trascina **Input (Casella di controllo)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Input (Pulsante di opzione)**

![Schermata VisualStudioHTMLpageRadioButton](../../ide/reference/media/vxradio.gif)

Consente di inserire un elemento `input` di `type="radio"`. Per modificare il testo visualizzato, modificare la proprietà `name`. Per impostazione predefinita, come primo pulsante di opzione viene inserito `id="Radio1"`, come secondo `id="Radio2"` e così via.

Quando si trascina **Input (Pulsante di opzione)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Input (Nascosto)**

![Elemento nascosto pagina HTML](../../ide/reference/media/vxhidden.gif)

Consente di inserire un elemento `input` di `type="hidden"`. Per impostazione predefinita, come primo campo nascosto viene inserito `id="Hidden1"`, come secondo `id="Hidden2"` e così via.

Quando si trascina **Input (Nascosto)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Area di testo**

![Area del testo della barra degli strumenti in una pagina HTML](../../ide/reference/media/vxtextarea.gif)

Consente di inserire un elemento `textarea`. È possibile ridimensionare l'area di testo oppure usare le barre di scorrimento per visualizzare il testo che si estende oltre l'area di visualizzazione. Per modificare il testo predefinito visualizzato, modificare l'attributo `value`. Per impostazione predefinita, come prima area di testo viene inserito `id="textarea1"`, come seconda `id=" textarea 2"` e così via.

Quando si trascina **Area di testo** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> È consigliabile convalidare tutto l'input degli utenti. Per altre informazioni, vedere [Validating User Input in ASP.NET Web Pages (Razor) Sites](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites) (Convalida dell'input utente nelle pagine Web ASP.NET).

**Tabella**

![Schermata HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif)

Consente di inserire un elemento `table`.

Quando si trascina **Tabella** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Immagine**

![Elemento immagine pagina HTML](../../ide/reference/media/vximage.gif)

Consente di inserire un elemento `img`. Modificare questo elemento per specificare il testo `src` e `alt`.

Quando si trascina **Immagine** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<img alt="" src="">
```

**Select**

![Controllo Dropdown della casella degli strumenti di una pagina HTML](../../ide/reference/media/vxdropdown.gif)

Consente di inserire un elemento `select` a discesa senza attributo `size`. Per impostazione predefinita, come prima casella di riepilogo viene inserito `id="select1"`, come seconda `id="select2"` e così via.

Quando si trascina **Seleziona** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<select id="select1" name="select1"><option selected></option></select>
```

È possibile creare un elemento `select` aumentando il valore della proprietà Size.

**Regola orizzontale**

![Elemento righello orizzontale pagina HTML](../../ide/reference/media/vxhorizontal.gif)

Consente di inserire un elemento `hr`. Per aumentare lo spessore della linea, modificare l'attributo `size`.

Quando si trascina **Righello orizzontale** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<hr width="100%" size=1>
```

**Div**

![Etichetta pagina HTML](../../ide/reference/media/vxlabel.gif)

Consente di inserire un elemento `div` che include un attributo `ms_positioning="FlowLayout"`. Tranne che per i valori relativi a larghezza e altezza, questo elemento è identico a un pannello di layout flusso. Per formattare il testo contenuto nell'elemento `div`, aggiungere un attributo `class="stylename"` al tag di apertura.

Quando si trascina **Div** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Vedi anche

- [Casella degli strumenti](../../ide/reference/toolbox.md)
