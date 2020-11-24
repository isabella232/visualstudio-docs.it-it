---
title: Uso dei controlli HTML5 nei test codificati dell'interfaccia utente
description: Informazioni sul supporto dei test codificati dell'interfaccia utente per i controlli HTML5 inclusi in Internet Explorer 9 e Internet Explorer 10.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d902d31b0d417c32b7b3e1a2067a8bb5bcf77451
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598380"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Uso dei controlli HTML5 nei test codificati dell'interfaccia utente

I test codificati dell'interfaccia utente includono il supporto per alcuni dei controlli HTML5 inclusi in Internet Explorer 9 e Internet Explorer 10.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requirements**

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
|**Riproduzione audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Riprodurre l' \<name> audio da 00:00:00|HtmlAudio.Play(TimeSpan)|
|**Ricercare un punto specifico dell'audio**|Cerca \<name> audio su 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**Sospendere la riproduzione dell'audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Sospendere l' \<name> audio alle 00:01:53|HtmlAudio.Pause(TimeSpan)|
|**Disattivare il volume dell'audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Disattiva \<name> audio|HtmlAudio.Mute()|
|**Riattivare il volume dell'audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Disattiva \<name> audio|HtmlAudio.Unmute()|
|**Modificare il volume dell'audio**|Imposta volume dell' \<name> audio su 79%|HtmlAudio.SetVolume(float)|

Vedere [HTMLAudioElement](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement) per un elenco delle proprietà in cui è possibile aggiungere un'asserzione.

**Proprietà di ricerca:** Le proprietà di ricerca per `HtmlAudio` sono `Id` , `Name` e `Title` .

**Proprietà filtro:** Le proprietà di filtro `HtmlAudio` per `Src` sono `Class` , `ControlDefinition` e `TagInstance` .

> [!NOTE]
> L'intervallo di tempo per la ricerca e la sospensione può essere significativo. Durante la riproduzione, il test codificato dell'interfaccia utente attenderà fino all'ora specificata in `(TimeSpan)` prima di sospendere l'audio. Se, in alcune circostanze speciali, l'ora specificata passa prima di fare clic sul comando Sospendi, verrà generata un'eccezione.

## <a name="video-control"></a>Controllo video
**Controllo Video**: le azioni nel controllo Video HTML5 vengono registrate e riprodotte correttamente.

![Controllo video HTML5](../test/media/codedui_html5_video.png)

|Azione|Registrazione|Codice generato|
|-|---------------|-|
|**PlayVideo**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Riprodurre \<name> video da 00:00:00|HtmlVideo.Play(TimeSpan)|
|**Ricercare un punto specifico nel video**|Cerca il \<name> video a 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Sospendere la riproduzione del video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Sospendere il \<name> video a 00:01:53|HtmlVideo.Pause(TimeSpan)|
|**Disattivare il volume del video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Disattiva \<name> video|HtmlVideo.Mute()|
|**Riattivare il volume del video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida del controllo.|Disattiva \<name> video|HtmlVideo.Unmute()|
|**Modificare il volume del video**|Imposta volume del \<name> video su 79%||

Vedere [HTMLVideoElement](https://developer.mozilla.org/docs/Web/HTML/Element/video) per un elenco delle proprietà in cui è possibile aggiungere un'asserzione.

**Proprietà di ricerca:** Le proprietà di ricerca per `HtmlVideo` sono `Id` , `Name` e `Title` .

**Proprietà filtro:** Le proprietà di filtro `HtmlVideo` per `Src` sono `Poster` , `Class` , `ControlDefinition` e `TagInstance` .

> [!NOTE]
> Se si riavvolge o si fa avanzare rapidamente il video usando le etichette -30s o +30s, il video verrà aggregato in modo da passare all'ora appropriata.

## <a name="progressbar"></a>ProgressBar
**Controllo ProgressBar**: si tratta di un controllo con cui non si può interagire. È possibile aggiungere asserzioni nelle proprietà `Value` e `Max` di questo controllo. Per altre informazioni, vedere [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

![Controllo ProgressBar HTML5](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Vedere anche

- [Elementi HTML](https://developer.mozilla.org/docs/Web/HTML/Element)
- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
- [Creare test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md)
- [Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
