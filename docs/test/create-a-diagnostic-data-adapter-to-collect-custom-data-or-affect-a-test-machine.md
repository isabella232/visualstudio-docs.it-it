---
title: Creare un adattatore dati di diagnostica per i test
description: Informazioni su come scrivere codice per eseguire attività in punti specifici dell'esecuzione dei test usando le API fornite all'interno di Visual Studio Enterprise.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 80fdb3453ec3f33ac00ea678f89b2b6d542e3895
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148649"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Creare un adattatore dati di diagnostica per raccogliere dati personalizzati o influire su un computer di test

È possibile creare un adattatore dati di diagnostica personalizzato per raccogliere dati durante un test oppure per influire sul computer di test come parte del test. Potrebbe essere necessario, ad esempio, raccogliere i file di log creati dall'applicazione sottoposta a test e allegarli ai risultati del test oppure eseguire i test quando lo spazio su disco sul computer è insufficiente. Usando le API disponibili in Visual Studio Enterprise, è possibile scrivere codice per eseguire attività in punti specifici dell'esecuzione dei test. È possibile, ad esempio, eseguire le attività prima di iniziare a eseguire i test, dopo il completamento dei test, prima o dopo l'esecuzione di ogni singolo test.

::: moniker range="vs-2017"
È possibile fornire input predefinito all'adattatore dati di diagnostica personalizzato tramite un file delle impostazioni di configurazione. È possibile, ad esempio, fornire informazioni sulla posizione del file che si desidera raccogliere e allegare ai risultati del test o su quanto spazio su disco si desidera lasciare nel sistema. È possibile configurare questi dati per ciascuna impostazione di test creata. Possono essere visualizzati e modificati tramite l'editor predefinito disponibile in Microsoft test Manager oppure è possibile creare un controllo utente personalizzato da usare come editor. Qualsiasi modifica apportata alla configurazione dell'adattatore nell'editor viene archiviata con le impostazioni di test.
::: moniker-end

::: moniker range=">=vs-2019"
È possibile fornire input predefinito all'adattatore dati di diagnostica personalizzato tramite un file delle impostazioni di configurazione. È possibile, ad esempio, fornire informazioni sulla posizione del file che si desidera raccogliere e allegare ai risultati del test o su quanto spazio su disco si desidera lasciare nel sistema. È possibile configurare questi dati per ciascuna impostazione di test creata. È possibile creare un controllo utente personalizzato da usare come editor. Qualsiasi modifica apportata alla configurazione dell'adattatore nell'editor viene archiviata con le impostazioni di test.
::: moniker-end

Se i test vengono eseguiti da Visual Studio, è necessario impostare come attive queste impostazioni di test. Per altre informazioni sulle impostazioni di test, vedere [Raccogliere informazioni di diagnostica usando le impostazioni di test.](../test/collect-diagnostic-information-using-test-settings.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Attività

Utilizzare gli argomenti seguenti per creare adattatori dati di diagnostica:

|Attività|Argomenti correlati|
|-|-----------------------|
|**Creazione di un adattatore dati di diagnostica:** si crea un adattatore dati di diagnostica creando una libreria di classi, quindi si usano le API dell'adattatore dati di diagnostica per raccogliere le informazioni necessarie o per influire su un sistema di test usato per eseguire i test.|-   [Procedura: Creare un adattatore dati di diagnostica](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Selezione di un adattatore dati di diagnostica personalizzato da usare durante l'esecuzione dei test:** è possibile stabilire quale adattatore dati di diagnostica usare per le impostazioni test, in modo che venga usato quando si eseguono i test.|-   [Raccogliere dati di diagnostica durante il test (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)<br />-   [Raccogliere dati di diagnostica nei test manuali (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)|

## <a name="see-also"></a>Vedi anche

- [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md)