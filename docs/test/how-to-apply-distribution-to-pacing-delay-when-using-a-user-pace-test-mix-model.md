---
title: Applicare la distribuzione al ritardo velocità per i test di carico
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d3ef8ecfefd1d614570b4d73808d3e5736d77230
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932560"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Procedura: Applicare la distribuzione al ritardo velocità per un modello di combinazione di test basato sulla velocità dell'utente

Dopo aver creato il test di carico mediante la **Creazione guidata test di carico**, è possibile usare l'Editor test di carico per modificare le proprietà dello scenario in modo da soddisfare le necessità e gli obiettivi di test specifici.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

La proprietà **Applica distribuzione a ritardo velocità** viene impostata tramite la finestra **Proprietà**. Le proprietà degli scenari dei test di carico vengono modificate tramite l'Editor test di carico.

> [!NOTE]
> La proprietà **Applica distribuzione a ritardo velocità** si applica solo se la *combinazione di test di carico* viene configurata in base alla velocità dell'utente. Per altre informazioni, vedere [Modifica di modelli di combinazione di test per specificare la probabilità che un utente virtuale esegua un test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

È possibile impostare il valore della proprietà **Applica distribuzione a ritardo velocità** su True o False:

- **True**: lo scenario applicherà ritardi di distribuzione statistici normali specificati dal valore nella colonna **Test per utente all'ora** nella finestra di dialogo **Modifica combinazione di test**. Per altre informazioni, vedere [Modifica di modelli di combinazione di test per specificare la probabilità che un utente virtuale esegua un test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Si supponga ad esempio di avere il valore **Test per utente all'ora** nella finestra di dialogo **Modifica combinazione di test** impostato su 2 utenti all'ora. Se la proprietà **Applica distribuzione a ritardo velocità** è impostata su **True**, una distribuzione statistica normale viene applicata al tempo di attesa tra i test. I test verranno ancora eseguiti in numero di 2 all'ora, ma non trascorrerà necessariamente un ritardo di 30 minuti tra le esecuzioni. Il primo test potrebbe venire eseguito dopo 4 minuti e il secondo test dopo 45 minuti.

- **False**: i test verranno eseguiti con la velocità specificata con il valore della colonna **Test per utente all'ora** della finestra di dialogo **Modifica combinazione di test**. Per altre informazioni, vedere [Modifica di modelli di combinazione di test per specificare la probabilità che un utente virtuale esegua un test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Si supponga ad esempio di avere il valore **Test per utente all'ora** nella finestra di dialogo **Modifica combinazione di test** impostato su 2 utenti all'ora. Se la proprietà **Applica distribuzione a ritardo velocità** è impostata su **False**, non si prevede alcun intervallo di tolleranza nell'esecuzione dei test. Il test verrà eseguito ogni 30 minuti. In questo modo si è certi che verranno eseguiti 2 test all'ora.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Per specificare l'impostazione della proprietà Applica distribuzione a ritardo velocità per uno scenario

1. Aprire un test di carico.

   Viene visualizzato l'**Editor test di carico**. Verrà visualizzato l'albero del test di carico.

2. Nella cartella **Scenari** dell'albero del test di carico selezionare il nodo dello scenario a cui si vuole applicare la distribuzione della velocità.

3. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

   Le categorie e le proprietà dello scenario vengono visualizzate nella finestra **Proprietà**.

4. Come valore della proprietà **Applica distribuzione a ritardo velocità** selezionare **True** o **False**.

5. Selezionare **File** > **Salva**. È ora possibile eseguire il test di carico usando il nuovo valore di **Applica distribuzione a ritardo velocità**.

## <a name="see-also"></a>Vedere anche

- [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md)
- [Procedura dettagliata: Creare ed eseguire un test di carico](../test/walkthrough-create-and-run-a-load-test.md)
- [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)