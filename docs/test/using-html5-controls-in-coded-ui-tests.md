---
title: Uso dei controlli HTML5 nei test codificati dell'interfaccia utente
description: Informazioni sul supporto dei test codificati dell'interfaccia utente per i controlli HTML5 inclusi in Internet Explorer 9 e Internet Explorer 10.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: aa961c87dfae8dc740fa72d6915b27f3a735da1a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054015"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Uso dei controlli HTML5 nei test codificati dell'interfaccia utente

I test codificati dell'interfaccia utente includono il supporto per alcuni dei controlli HTML5 inclusi in Internet Explorer 9 e Internet Explorer 10.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requisiti**

- Visual Studio Enterprise

> [!WARNING]
> Nelle versioni precedenti a Internet Explorer 10, è possibile eseguire test codificati dell'interfaccia utente con un livello di privilegi più alto rispetto a quello del processo di Internet Explorer. Quando si eseguono test codificati dell'interfaccia utente in Internet Explorer 10, sia il test codificato dell'interfaccia utente che il processo di Internet Explorer devono avere lo stesso livello di privilegi. Infatti le funzionalità di AppContainer sono più sicure in Internet Explorer 10.

> [!WARNING]
> Un test codificato dell'interfaccia utente creato in Internet Explorer 10 potrebbe non funzionare in Internet Explorer 9 o Internet Explorer 8. Questo perché Internet Explorer 10 include controlli HTML5 come audio, video, ProgressBar e dispositivo di scorrimento. Questi controlli HTML5 non sono riconosciuti da Internet Explorer 9 o da Internet Explorer 8. Analogamente, il test codificato dell'interfaccia utente creato in Internet Explorer 9 potrebbe includere alcuni controlli HTML5 non riconosciuti in Internet Explorer 8.

## <a name="audio-control"></a>Controllo audio

**Controllo Audio**: le azioni nel controllo Audio HTML5 vengono registrate e riprodotte correttamente.

![Controllo audio HTML5](../test/media/codedui_html5_audio.png)

|Azione|Registrazione|Codice generato|
|-|---------------|-|
|**Riprodurre l'audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Riproduci \<name> audio da 00:00:00|HtmlAudio.Play(TimeSpan)|
|**Ricercare un punto specifico dell'audio**|Cercare \<name> l'audio in 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**Sospendere la riproduzione dell'audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|\<name>Sospendi audio alle 00:01:53|HtmlAudio.Pause(TimeSpan)|
|**Disattivare il volume dell'audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Disattivare \<name> l'audio|HtmlAudio.Mute()|
|**Riattivare il volume dell'audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Riattivare \<name> l'audio|HtmlAudio.Unmute()|
|**Modificare il volume dell'audio**|Impostare il volume \<name> dell'audio al 79%|HtmlAudio.SetVolume(float)|

Vedere [HTMLAudioElement](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement) per un elenco delle proprietà in cui è possibile aggiungere un'asserzione.

**Proprietà di ricerca:** Le proprietà di ricerca `HtmlAudio` per sono , e `Id` `Name` `Title` .

**Proprietà filtro:** Le proprietà del filtro `HtmlAudio` per sono , e `Src` `Class` `ControlDefinition` `TagInstance` .

> [!NOTE]
> L'intervallo di tempo per la ricerca e la sospensione può essere significativo. Durante la riproduzione, il test codificato dell'interfaccia utente attenderà fino all'ora specificata in `(TimeSpan)` prima di sospendere l'audio. Se, in alcune circostanze speciali, l'ora specificata passa prima di fare clic sul comando Sospendi, verrà generata un'eccezione.

## <a name="video-control"></a>Controllo video
**Controllo Video**: le azioni nel controllo Video HTML5 vengono registrate e riprodotte correttamente.

![Controllo video HTML5](../test/media/codedui_html5_video.png)

|Azione|Registrazione|Codice generato|
|-|---------------|-|
|**PlayVideo**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Riproduci \<name> video da 00:00:00|HtmlVideo.Play(TimeSpan)|
|**Ricercare un punto specifico nel video**|Cercare \<name> video in 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Sospendere la riproduzione del video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Sospendere \<name> il video alle 00:01:53|HtmlVideo.Pause(TimeSpan)|
|**Disattivare il volume del video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Disattivare \<name> l'audio del video|HtmlVideo.Mute()|
|**Riattivare il volume del video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Riattivare \<name> l'audio del video|HtmlVideo.Unmute()|
|**Modificare il volume del video**|Impostare il volume \<name> del video sul 79%||

Vedere [HTMLVideoElement](https://developer.mozilla.org/docs/Web/HTML/Element/video) per un elenco delle proprietà in cui è possibile aggiungere un'asserzione.

**Proprietà di ricerca:** Le proprietà di ricerca `HtmlVideo` per sono , e `Id` `Name` `Title` .

**Proprietà filtro:** Le proprietà del filtro `HtmlVideo` per sono , , e `Src` `Poster` `Class` `ControlDefinition` `TagInstance` .

> [!NOTE]
> Se si riavvolge o si fa avanzare rapidamente il video usando le etichette -30s o +30s, il video verrà aggregato in modo da passare all'ora appropriata.

## <a name="progressbar"></a>ProgressBar
**Controllo ProgressBar**: si tratta di un controllo con cui non si può interagire. È possibile aggiungere asserzioni nelle proprietà `Value` e `Max` di questo controllo. Per altre informazioni, vedere [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

![Controllo ProgressBar HTML5](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Vedi anche

- [Elementi HTML](https://developer.mozilla.org/docs/Web/HTML/Element)
- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
- [Creare test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md)
- [Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
