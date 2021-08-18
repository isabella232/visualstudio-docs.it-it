---
title: Combinazione di test per uno scenario di test di carico
description: Informazioni su come modificare la combinazione di test di uno scenario, ovvero una combinazione della selezione delle prestazioni Web e degli unit test e della distribuzione di tali test.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, adding tests
- test mix
- load tests, test mix
- load tests, removing tests
ms.assetid: 303e1d70-5d98-424a-b51e-e0898e16d3f8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 8990b05e0216e9f600aeb1236d7ce847341e9e0a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135806"
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>Modificare la combinazione di test per specificare quali test delle prestazioni Web, unit test e test codificati dell'interfaccia utente includere in uno scenario di test di carico

La *combinazione di* test di uno scenario è una combinazione della selezione di test delle prestazioni Web e unit test contenuti nello scenario e della distribuzione di tali test nello scenario. La distribuzione è un'impostazione che è possibile specificare in relazione alla probabilità che un determinato test venga selezionato da un utente virtuale durante l'esecuzione di un test di carico.

Dopo che un set di test è stato aggiunto a un test di carico, la *combinazione di test* ha le stesse modalità di altre opzioni di combinazione. Un utente virtuale seleziona casualmente un test in base alla probabilità specificata nella combinazione. Se, ad esempio, sono disponibili due test, ognuno con un valore del 50% nella combinazione, un nuovo utente virtuale sceglierà di eseguire il primo test circa metà delle volte. In una combinazione 50/50, se un test è lungo e l'altro è corto, il carico maggiore sarà prodotto dal test più lungo.

Dopo aver aggiunto test alla combinazione, è possibile rimuoverli. È inoltre possibile modificare la distribuzione della combinazione di test utilizzando il controllo combinazione. Il controllo combinazione consente di regolare facilmente la distribuzione dei test in uno scenario.

> [!NOTE]
> La distribuzione è una misura della probabilità che un determinato test sarà selezionato da un utente virtuale durante l'esecuzione di un test di carico. La distribuzione viene espressa sotto forma di percentuale. Pertanto, la somma dei numeri della distribuzione per tutti i test contenuti in uno scenario è pari a 100. Se ad esempio uno scenario contiene un solo test, la distribuzione per quel test è 100%.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>Aggiungere nuovi test a una combinazione di test in uno scenario esistente

Quando si crea un nuovo scenario usando la **Creazione guidata test di carico** è possibile specificare i test delle prestazioni Web e gli unit test da aggiungere alla combinazione di test del nuovo scenario.

È possibile aggiungere altri test delle prestazioni Web e unit test alla combinazione di test dello scenario usando l'**Editor test di carico**.

![Aggiunta di un test a un test di carico esistente](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>Per aggiungere più test a uno scenario esistente

1. Aprire un test di carico.

2. Nella finestra **Editor test di carico** fare clic con il pulsante destro del mouse su uno scenario esistente e quindi **scegliere Aggiungi test**.

     Verrà visualizzata la finestra di dialogo **Aggiungi test**. È possibile aggiungere allo scenario tutti i test delle prestazioni Web, gli unit test e i test codificati dell'interfaccia utente della soluzione non ancora aggiunti.

3. Nel riquadro **Test disponibili selezionare** le prestazioni Web, l'unità e i test codificati dell'interfaccia utente da aggiungere. Fare clic sulla freccia destra per aggiungere i test al riquadro **Test selezionati**.

4. Al termine dell'aggiunta dei test, scegliere **OK**.

     I test sono stati aggiunti alla combinazione di test. Una nuova distribuzione viene assegnata automaticamente ai test nella combinazione.

5. (Facoltativo) Modificare il controllo combinazione per specificare la distribuzione dei test. Per altre informazioni, vedere [Informazioni sul controllo combinazione](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

## <a name="remove-tests-from-a-scenario"></a>Rimuovere test da uno scenario
![Rimozione di un test da un test di carico esistente](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>Per rimuovere test da uno scenario

1. Aprire un test di carico.

2. **Nell'Editor test di carico** del test di carico fare clic con il pulsante destro del mouse nello scenario da cui si vuole rimuovere un test e scegliere **Modifica combinazione di test**. Verrà visualizzata la finestra di dialogo **Modifica combinazione di test**.

3. Selezionare il test delle prestazioni Web, dell'unità o dell'interfaccia utente codificato nella griglia e quindi scegliere **Rimuovi**.

    > [!NOTE]
    > Dopo aver rimosso il test, regolare la combinazione di test in base alla distribuzione preferita.

4. Al termine della rimozione dei test, scegliere **OK**.

## <a name="about-the-mix-control"></a><a name="EditingTestMixAboutMixControl"></a> Informazioni sul controllo Combinazione
Il controllo Mix consente di regolare la percentuale di carico distribuita tra test, tipi di browser o tipi di rete in uno scenario di test di carico. I valori percentuali vengono modificati spostando i dispositivi di scorrimento. Con la regolazione della combinazione di test si specifica la probabilità che un utente virtuale esegua un determinato test in uno scenario di test di carico.

Quando si sposta un dispositivo di scorrimento, i valori in percentuale di tutti gli elementi disponibili variano. Se gli elementi sono più di due, la quantità aggiunta o rimossa viene distribuita in modo uniforme tra gli altri elementi. È possibile eseguire l'override di questo comportamento. Se si seleziona la casella di controllo nella colonna del blocco per un particolare elemento, il valore percentuale specificato per tale elemento verrà bloccato. Quindi, quando si sposta un dispositivo di scorrimento, il quantità aggiunta o rimossa viene applicata solo agli eventuali elementi non bloccati rimanenti.

Il pulsante **Distribuisci** consente di allocare le percentuali in modo uniforme tra tutti gli elementi. In presenza di tre elementi, ad esempio, se si sceglie **Distribuisci** le percentuali verranno impostate su 34, 33 e 33.

> [!WARNING]
> Il pulsante **Distribuisci** esegue l'override degli eventuali elementi bloccati.

È anche possibile digitare i valori percentuali direttamente nella colonna **%** anziché usare i dispositivi di scorrimento. Se si immette direttamente un valore in percentuale, gli altri elementi non verranno regolati automaticamente.

> [!NOTE]
> I dispositivi di scorrimento sono disabilitati quando il totale non è al 100% o quando i valori percentuali immessi nella colonna **%** sono decimali.

Quando si immettono manualmente le percentuali, assicurarsi che la somma di tutti gli elementi sia 100%. Quando si salva una combinazione, se la somma non è pari al 100%, verrà richiesto di accettare i valori percentuali così come sono o di tornare indietro e regolarli. Se si sceglie di accettarle così come sono, le percentuali verranno ripartite proporzionalmente al 100%.  Se ad esempio si dispone di due elementi che sono stati impostati manualmente su 80% e 40%, il primo elemento verrà impostato su 66,67% (80 diviso 120) mentre il secondo su 33,33% (40 diviso 120).

## <a name="see-also"></a>Vedi anche

- [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md)
