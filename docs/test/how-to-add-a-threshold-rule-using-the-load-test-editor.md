---
title: Aggiungere una regola di soglia per i test di carico in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: f68ab9b183119c18bed51bb7faaa86993d7f34ce
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179879"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Procedura: Aggiungere una regola di soglia usando l'Editor test di carico

Le regole di soglia nei test di carico consentono di confrontare il valore di un contatore delle prestazioni con il valore di una costante o di un altro contatore delle prestazioni.

## <a name="to-add-a-threshold-rule"></a>Per aggiungere una regola di soglia

1.  Aprire un test di carico.

2.  Nell'Editor test di carico espandere il nodo **Insiemi di contatori**.

3.  Espandere una delle **Categorie contatori** in uno degli Insiemi di contatori. Ad esempio, è possibile selezionare **LoadTest:Scenario**. Espandere il nodo.

4.  Fare clic con il pulsante destro del mouse sui contatori, ad esempio **Carico utente**, in **LoadTest:Scenario**. Selezionare **Aggiungi regola di soglia**.

     Viene visualizzata la finestra di dialogo **Aggiungi regola di soglia**.

5.  È possibile scegliere tra due tipi di regole: **Confronta costante** e **Confronta contatori**. Selezionare il tipo appropriato e impostare i valori.

    > [!NOTE]
    > Impostare la proprietà **Avvisa se supera** su **True** per indicare che il superamento della soglia è un problema oppure su **False** per indicare che il non raggiungimento della soglia è un problema.

## <a name="see-also"></a>Vedere anche

- [Analisi delle violazioni delle regole di soglia](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
