---
title: Aggiungere parametri di contesto a un'impostazione di esecuzione test di carico
description: Informazioni su come creare parametri di contesto da usare in un'impostazione di esecuzione del test di carico usando il Editor test di carico, che consente di parametrizzare una stringa.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: b128d2b12447b1547237060ab6e18f899bc60eef6ab489ccd1f7f57a78f33b94
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121299825"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Procedura: Aggiungere parametri di contesto a un'impostazione di esecuzione test di carico

Dopo aver creato il test di carico mediante la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà degli scenari in modo da soddisfare le necessità e gli obiettivi di test specifici.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Per un elenco completo delle proprietà delle impostazioni esecuzione test e delle relative descrizioni, vedere Proprietà [delle impostazioni esecuzione test di carico.](../test/load-test-run-settings-properties.md)

È possibile creare parametri di contesto da utilizzare in un'impostazione di esecuzione del test di carico utilizzando l'Editor test di carico. I parametri di contesto consentono di parametrizzare una stringa.

Si supponga che il test di carico contenga un test delle prestazioni Web che già usa un URL di server Web con parametri tramite un parametro di contesto. È possibile aggiungere un parametro di contesto a un'impostazione di esecuzione del test di carico che usa lo stesso valore di nome usato nel test delle prestazioni Web. In questo modo il test delle prestazioni Web verrà mappato a un server diverso quando si esegue il test di carico. Ad esempio, se il test di carico include un test delle prestazioni Web che usa un parametro di contesto denominato WebServer1 per il nome del server Web nell'URL, se si specifica quindi un parametro di contesto nell'impostazione di esecuzione del test di carico che sia anche denominato WebServer1, il test di carico utilizzerà il parametro di contesto assegnato nell'impostazione di esecuzione del test di carico. In altre parole, se il test delle prestazioni Web incluso nel test di carico usa un parametro di contesto con lo stesso nome di un parametro di contesto nel test di carico, il parametro di contesto nel test di carico eseguirà l'override del parametro di contesto usato nel test delle prestazioni Web.

> [!WARNING]
> Prestare attenzione a non eseguire l'override accidentale del parametro di contesto di un test delle prestazioni Web quando si usano parametri di contesto in un'impostazione di esecuzione test. Evitare di utilizzare gli stessi nomi per i parametri di contesto a meno che lo si faccia intenzionalmente.

Se si assegna il valore del parametro di contesto Webserver1 a `http://CorporateStagingWebServer`, è possibile usare `WebServer1` in tutto il test di carico e cambiare facilmente il valore in un altro server Web in qualsiasi momento.

Inoltre, assegnando valori diversi a un parametro di contesto utilizzando lo stesso nome nelle diverse impostazioni di esecuzione del test di carico, è possibile eseguire il test di carico in ambienti diversi:

- Impostazione di esecuzione server Web aziendale di gestione temporanea: il parametro di contesto denominato `WebServer1=http://CorporateStagingWebServer`

- Impostazione di esecuzione server Web aziendale di produzione: il parametro di contesto denominato `WebServer1=http://CorporateProductionWebServer`

  **Modifica dell'impostazione di esecuzione test dalla riga di comando**

  Se si desidera utilizzare impostazioni di esecuzione test differenti dalla riga di comando per sfruttare la strategia dei parametri di contesto, utilizzare i comandi seguenti:

  **Set Test.UseRunSetting= CorporateStagingWebServer**

  -e-

  **mstest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Per aggiungere un parametro di contesto a un'impostazione di esecuzione

1. Aprire un test di carico.

2. Espandere la cartella **Impostazioni di esecuzione** nell'albero del test di carico dell'Editor test di carico.

3. Fare clic con il pulsante destro del mouse sulle impostazioni esecuzione test specifiche a cui si vuole aggiungere un parametro di contesto e scegliere **Aggiungi parametro di contesto**.

     Un nuovo parametro di contesto viene aggiunto alla cartella **Parametri di contesto** nella cartella **Impostazioni di esecuzione** nell'albero del test di carico.

     -oppure-

     Se le impostazioni esecuzione test già contengono una cartella **Parametri di contesto**, è possibile fare clic con il pulsante destro del mouse sulla cartella e scegliere **Aggiungi parametro di contesto**.

4. Nella finestra **Proprietà** modificare il valore di **Nome** in base alle esigenze, ad esempio WebServer1. Nella **finestra** Proprietà modificare **Valore** nel parametro che si vuole usare, ad esempio `http://CorporateStagingWebServer` .

5. (Facoltativo) Ripetere i passaggi da 3 a 5 e usare una stringa diversa per la **proprietà Value** , ad esempio `http://CorporateProductionWebServer` .

6. Scegliere quali impostazioni esecuzione test devono essere attive. Aprire il menu di scelta rapida nelle impostazioni esecuzione test e scegliere **Imposta come attivo**.

## <a name="see-also"></a>Vedi anche

- [Configurare le impostazioni di esecuzione dei test di carico](../test/configure-load-test-run-settings.md)
