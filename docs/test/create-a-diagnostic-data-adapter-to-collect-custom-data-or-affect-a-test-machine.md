---
title: Creare un adattatore dati di diagnostica per i test
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: 59874cd8b7f34e8af8f91a91d8ed052351a8522c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54969941"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Creare un adattatore dati di diagnostica per raccogliere dati personalizzati o influire su un computer di test

È possibile creare un adattatore dati di diagnostica personalizzato per raccogliere dati durante un test oppure per influire sul computer di test come parte del test. Potrebbe essere necessario, ad esempio, raccogliere i file di log creati dall'applicazione sottoposta a test e allegarli ai risultati del test oppure eseguire i test quando lo spazio su disco sul computer è insufficiente. Usando le API disponibili in Visual Studio Enterprise, è possibile scrivere codice per eseguire attività in punti specifici dell'esecuzione dei test. È possibile, ad esempio, eseguire le attività prima di iniziare a eseguire i test, dopo il completamento dei test, prima o dopo l'esecuzione di ogni singolo test.

È possibile fornire input predefinito all'adattatore dati di diagnostica personalizzato tramite un file delle impostazioni di configurazione. È possibile, ad esempio, fornire informazioni sulla posizione del file che si desidera raccogliere e allegare ai risultati del test o su quanto spazio su disco si desidera lasciare nel sistema. È possibile configurare questi dati per ciascuna impostazione di test creata. Possono essere visualizzati e modificati tramite l'editor predefinito disponibile in Microsoft test Manager oppure è possibile creare un controllo utente personalizzato da usare come editor. Qualsiasi modifica apportata alla configurazione dell'adattatore nell'editor viene archiviata con le impostazioni di test.

Se i test vengono eseguiti da Visual Studio, è necessario impostare come attive queste impostazioni di test. Per altre informazioni sulle impostazioni test, vedere [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Attività

Utilizzare gli argomenti seguenti per creare adattatori dati di diagnostica:

|Attività|Argomenti correlati|
|-|-----------------------|
|**Creazione di un adattatore dati di diagnostica:** creare un adattatore dati di diagnostica creando una libreria di classi. Usare quindi le API dell'adattatore dati di diagnostica per raccogliere le informazioni desiderate o per influire sul sistema di test usato per eseguire i test.|-   [Procedura: Creare un adattatore dati di diagnostica](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Selezione di un adattatore dati di diagnostica personalizzato da usare durante l'esecuzione dei test:** è possibile stabilire quale adattatore dati di diagnostica usare per le impostazioni test, in modo che venga usato quando si eseguono i test.|-   [Raccogliere dati di diagnostica durante i test (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)<br />-   [Raccogliere dati di diagnostica nei test manuali (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|

## <a name="see-also"></a>Vedere anche

- [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md)