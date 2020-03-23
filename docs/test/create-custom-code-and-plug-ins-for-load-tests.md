---
title: Creare codice personalizzato e plug-in per test di carico
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3519a593182c199cc9f7a92cfb77e9c79bd1a9ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590098"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Creare codice personalizzato e plug-in per test di carico

Un plug-in personalizzato usa codice scritto e collegato a un test di carico o a un test Web. È possibile usare l'API del test di carico e l'API del test Web per creare plug-in personalizzati per i test al fine di espandere le funzionalità predefinite. È possibile aggiungere più plug-in al test di carico.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Attività

|Attività|Argomenti correlati|
|-|-----------------------|
|**Creare un plug-in personalizzato per il test di carico**: è possibile usare l'API del test di carico per creare un plug-in personalizzato che consenta di aggiungere altre funzionalità di test al test di carico.|-   [Procedura: utilizzare l'API del test di caricoHow to: Use the load test API](../test/how-to-use-the-load-test-api.md)<br />-   [Procedura: creare un plug-in test di caricoHow to: Create a Load Test Plug-in](../test/how-to-create-a-load-test-plug-in.md)|
|**Creare un plug-in personalizzato per il test delle prestazioni Web:** È possibile utilizzare l'API del test delle prestazioni Web per creare un plug-in personalizzato per aggiungere ulteriori funzionalità di test al test delle prestazioni Web, anche a livello di richiesta. È anche possibile creare un test del servizio Web.<br /><br /> Inoltre, è possibile creare un plug-in di registrazione Web con il quale è possibile modificare un test delle prestazioni Web dopo che viene registrato, ma prima che venga visualizzato nel Visualizzatore risultati test prestazioni Web.|-   [Procedura: utilizzare l'API del test delle prestazioni WebHow to: Use the web performance test API](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Procedura: creare un plug-in test delle prestazioni WebHow to: Create a web performance test plug-in](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Procedura: creare un plug-in a livello di richiestaHow to: Create a request-level plug-in](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Procedura: creare un test del servizio WebHow to: Create a web service test](../test/how-to-create-a-web-service-test.md)<br />-   [Procedura: creare un plug-in di registrazioneHow to: Create a recorder plug-in](../test/how-to-create-a-recorder-plug-in.md)|
|**Aggiungere funzionalità dell'interfaccia utente al Visualizzatore risultati test prestazioni Web:** è possibile aggiungere altre funzionalità dell'interfaccia utente al Visualizzatore risultati test prestazioni Web usando un componente aggiuntivo di Visual Studio.|-   [Procedura: creare un componente aggiuntivo di Visual Studio per il visualizzatore risultati test delle prestazioni WebHow to: Create a Visual Studio add-in for the web performance test results viewer](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Creare un editor del corpo HTTP personalizzato:** è possibile creare un editor personalizzato per modificare le risposte XML HTTP stringa o binario di un servizio Web.|-   [Procedura: creare un editor del corpo HTTP personalizzato per l'editor test delle prestazioni WebHow to: Create a custom HTTP body editor for the web performance test editor](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Informazioni di riferimento

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Vedere anche

- [Analizzare i risultati dei test di caricoAnalyze load test results](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Generare ed eseguire un test delle prestazioni Web codificato](../test/generate-and-run-a-coded-web-performance-test.md)
