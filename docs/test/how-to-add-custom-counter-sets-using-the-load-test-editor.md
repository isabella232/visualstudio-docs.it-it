---
title: Aggiungere insiemi di contatori personalizzati per i test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 8f691c0eac38dae9e9f419335eb1d3ae87c693df
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>Procedura: aggiungere insiemi di contatori personalizzati utilizzando l'Editor test di carico

Quando si crea un test di carico usando la **Creazione guidata test di carico**, è necessario aggiungere un insieme di contatori iniziale. Ciò offre una serie di insiemi di contatori predefiniti per il test di carico.

> [!NOTE]
> Se i test di carico vengono distribuiti in computer remoti, viene eseguito il mapping dei contatori di controller e agenti ai relativi set. Per altre informazioni sull'utilizzo di computer remoti nel test di carico, vedere [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md).

I contatori vengono gestiti nell'**Editor test di carico**. Gli insiemi di contatori già aggiunti al test sono visibili nel nodo **Insiemi di contatori** del test di carico. Dopo aver creato un test di carico, è possibile aggiungervi i nuovi insiemi di contatori personalizzati.

![Insieme di contatori personalizzati](../test/media/loadtestcustomcounter.png "LoadTestCustomCounter")

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>Per aggiungere un insieme di contatori personalizzati a un test di carico

1.  Aprire un test di carico.

2.  Espandere il nodo **Insiemi di contatori**. Verranno visualizzati tutti gli insiemi di contatori aggiunti al test di carico.

3.  Fare clic con il pulsante destro del mouse sul nodo **Insiemi di contatori** e scegliere **Aggiungi insieme di contatori personalizzati**.

    > [!NOTE]
    > All'insieme di contatori viene assegnato un nome predefinito, ad esempio **Custom1**. È possibile modificare il nome usando la finestra **Proprietà**. Premere F4 per visualizzare la finestra **Proprietà**.

4.  Per aggiungere contatori all'insieme di contatori personalizzati, fare clic con il pulsante destro del mouse sul nuovo insieme di contatori e scegliere **Aggiungi contatori**. Per altre informazioni su come aggiungere i contatori, vedere [Procedura: Aggiungere i contatori agli insiemi di contatori](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md).

    > [!NOTE]
    > Per aggiungere un insieme di contatori personalizzati è anche possibile fare clic con il pulsante destro del mouse su un insieme esistente, scegliere Copia e quindi incollarlo nel nodo degli insiemi di contatori. I contatori aggiuntivi che vengono copiati ma non sono necessari possono essere eliminati. È possibile modificare il nome del nuovo insieme di contatori usando la finestra **Proprietà**.

## <a name="see-also"></a>Vedere anche

- [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Configurazione delle impostazioni esecuzione test di carico](../test/configure-load-test-run-settings.md)