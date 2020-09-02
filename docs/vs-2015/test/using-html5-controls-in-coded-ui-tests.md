---
title: Uso dei controlli HTML5 nei test codificati dell'interfaccia utente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: 19
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 029b547102863f4798ad261deb678c4d98596916
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657195"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Uso dei controlli HTML5 nei test codificati dell'interfaccia utente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I test codificati dell'interfaccia utente includono il supporto per alcuni dei controlli HTML5 inclusi in Internet Explorer 9 e Internet Explorer 10.

 **Requisiti**

- Visual Studio Enterprise

> [!WARNING]
> Nelle versioni precedenti a Internet Explorer 10, è possibile eseguire test codificati dell'interfaccia utente con un livello di privilegi più alto rispetto a quello del processo di Internet Explorer. Quando si eseguono test codificati dell'interfaccia utente in Internet Explorer 10, sia il test codificato dell'interfaccia utente che il processo di Internet Explorer devono avere lo stesso livello di privilegi. Infatti le funzionalità di AppContainer sono più sicure in Internet Explorer 10.

> [!WARNING]
> Un test codificato dell'interfaccia utente creato in Internet Explorer 10 potrebbe non funzionare in Internet Explorer 9 o Internet Explorer 8. Questo perché Internet Explorer 10 include controlli HTML5 come audio, video, ProgressBar e dispositivo di scorrimento. Questi controlli HTML5 non sono riconosciuti da Internet Explorer 9 o da Internet Explorer 8. Analogamente, il test codificato dell'interfaccia utente creato in Internet Explorer 9 potrebbe includere alcuni controlli HTML5 non riconosciuti in Internet Explorer 8.

## <a name="supported-html5-controls"></a>Controlli HTML5 supportati
 I test codificati dell'interfaccia utente includono il supporto per registrazione, riproduzione e convalida dei controlli HTML5 seguenti:

- [Controllo Audio](#audio-control)

- [Controllo Video](#video-control)

- [Dispositivo di scorrimento](#slider)

- [ProgressBar](#progressbar)

### <a name="audio-control"></a>Controllo audio
 **Controllo Audio**: le azioni nel controllo Audio HTML5 vengono registrate e riprodotte correttamente.

 ![Controllo audio HTML5](../test/media/codedui-html5-audio.png)

|Action|Registrazione|Codice generato|
|------------|---------------|--------------------|
|**Riproduzione audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Riprodurre l' \<name> audio da 00:00:00|HtmlAudio.Play(TimeSpan)|
|**Ricercare un punto specifico dell'audio**|Cerca \<name> audio su 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**Sospendere la riproduzione dell'audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Sospendere l' \<name> audio alle 00:01:53|HtmlAudio.Pause(TimeSpan)|
|**Disattivare il volume dell'audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Disattiva \<name> audio|HtmlAudio.Mute()|
|**Riattivare il volume dell'audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Disattiva \<name> audio|HtmlAudio.Unmute()|
|**Modificare il volume dell'audio**|Imposta volume dell' \<name> audio su 79%|HtmlAudio.SetVolume(float)|

 Le seguenti proprietà sono disponibili per HtmlAudio ed è possibile aggiungere un'asserzione in tutte:

```
string AutoPlay
string Controls
string CurrentSrc
string CurrentTime
string CurrentTimeAsString
string Duration
string DurationAsString
string Ended
string Loop
string Muted
string Paused
string PlaybackRate
string ReadyState
string Seeking
string Src
string Volume
```

 **Proprietà di ricerca:** Le proprietà di ricerca per `HtmlAudio` sono `Id` , `Name` e `Title` .

 **Proprietà filtro:** Le proprietà di filtro `HtmlAudio` per `Src` sono `Class` , `ControlDefinition` e `TagInstance` .

> [!NOTE]
> L'intervallo di tempo per la ricerca e la sospensione può essere significativo. Durante la riproduzione, il test codificato dell'interfaccia utente attenderà fino all'ora specificata in `(TimeSpan)` prima di sospendere l'audio. Se, in alcune circostanze speciali, l'ora specificata passa prima di fare clic sul comando Sospendi, verrà generata un'eccezione.

### <a name="video-control"></a>Controllo video
 **Controllo Video**: le azioni nel controllo Video HTML5 vengono registrate e riprodotte correttamente.

 ![Controllo video HTML5](../test/media/codedui-html5-video.png)

|Action|Registrazione|Codice generato|
|------------|---------------|--------------------|
|**PlayVideo**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Riprodurre \<name> video da 00:00:00|HtmlVideo.Play(TimeSpan)|
|**Ricercare un punto specifico nel video**|Cerca il \<name> video a 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Sospendere la riproduzione del video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Sospendere il \<name> video a 00:01:53|HtmlVideo.Pause(TimeSpan)|
|**Disattivare il volume del video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Disattiva \<name> video|HtmlVideo.Mute()|
|**Riattivare il volume del video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Disattiva \<name> video|HtmlVideo.Unmute()|
|**Modificare il volume del video**|Imposta volume del \<name> video su 79%||

 Tutte le proprietà di HtmlAudio sono disponibili per HtmlVideo. Inoltre, sono disponibili le seguenti tre proprietà. È possibile aggiungere un'asserzione in tutte.

```
string Poster
string VideoHeight
string VideoWidth

```

 **Proprietà di ricerca:** Le proprietà di ricerca per `HtmlVideo` sono `Id` , `Name` e `Title` .

 **Proprietà filtro:** Le proprietà di filtro `HtmlVideo` per `Src` sono `Poster` , `Class` , `ControlDefinition` e `TagInstance` .

> [!NOTE]
> Se si riavvolge o si fa avanzare rapidamente il video usando le etichette -30s o +30s, il video verrà aggregato in modo da passare all'ora appropriata.

### <a name="slider"></a>Dispositivo di scorrimento
 **Controllo Slider**: le azioni nel controllo Slider HTML5 vengono registrate e riprodotte correttamente.

 ![Controllo dispositivo di scorrimento HTML5](../test/media/codedui-html5-slider.png)

|Action|Registrazione|Codice generato|
|------------|---------------|--------------------|
|**Impostare una posizione nel dispositivo di scorrimento**|Imposta posizione su \<x> nel \<name> dispositivo di scorrimento|HtmlSlider. ValueAsNumber =\<x>|

 Le seguenti proprietà sono disponibili per HtmlSlider ed è possibile aggiungere un'asserzione in tutte:

```
string Disabled
string Max
string Min
string Required
string Step
string ValueAsNumber
```

### <a name="progressbar"></a>ProgressBar
 **Controllo ProgressBar**: si tratta di un controllo con cui non si può interagire. È possibile aggiungere asserzioni nelle proprietà `Value` e `Max` di questo controllo.

 ![Controllo ProgressBar HTML5](../test/media/codedui-html5-progressbar.png)

## <a name="see-also"></a>Vedere anche

- [Elementi HTML](https://www.w3schools.com/HTML/html_elements.asp)
- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
- [Creazione di test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Personalizzazione del test codificato dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)
- [Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
