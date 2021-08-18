---
title: Applicare la distribuzione al ritardo velocità per i test di carico
description: Informazioni su come impostare la proprietà Applica distribuzione a ritardo di pacing per un test di carico usando il Finestra Proprietà.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: db93dbbfadc33c8653bd44e6343cfcea5bbc5f1c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092553"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Procedura: Applicare la distribuzione al ritardo velocità per un modello di combinazione di test basato sulla velocità dell'utente

Dopo aver creato il test di carico usando il nuovo **Creazione guidata test di carico**, è possibile usare il Editor test di carico per modificare le proprietà dello scenario in modo da soddisfare le esigenze e gli obiettivi di test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

La proprietà Applica distribuzione a ritardo di **pacing** viene impostata tramite la **finestra** Proprietà. Le proprietà degli scenari dei test di carico vengono modificate tramite l'Editor test di carico.

> [!NOTE]
> La proprietà **Applica distribuzione a ritardo velocità** si applica solo se la *combinazione di test di carico* viene configurata in base alla velocità dell'utente. Per altre informazioni, vedere [Modificare modelli di combinazione di testo per specificare la probabilità che un utente virtuale esee in esecuzione un test.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

È possibile impostare il valore della proprietà **Applica distribuzione a ritardo velocità** su True o False:

- **True:** lo scenario applica ritardi di distribuzione statistici normali specificati dal valore nella colonna Test per utente **all'ora** della finestra di dialogo Modifica **combinazione** di test. Per altre informazioni, vedere [Modificare modelli di combinazione di testo per specificare la probabilità che un utente virtuale esee in esecuzione un test.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

     Si supponga, ad esempio, di avere il  valore Test per utente **all'ora** nella finestra di dialogo Modifica combinazione di test per il test impostato su due utenti all'ora. Se la proprietà **Applica distribuzione a ritardo velocità** è impostata su **True**, una distribuzione statistica normale viene applicata al tempo di attesa tra i test. I test verranno ancora eseguiti in numero di 2 all'ora, ma non trascorrerà necessariamente un ritardo di 30 minuti tra le esecuzioni. Il primo test potrebbe venire eseguito dopo 4 minuti e il secondo test dopo 45 minuti.

- **False**: i test verranno eseguiti con la velocità specificata con il valore della colonna **Test per utente all'ora** della finestra di dialogo **Modifica combinazione di test**. Per altre informazioni, vedere [Modificare modelli di combinazione di testo per specificare la probabilità che un utente virtuale esee in esecuzione un test.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

     Si supponga, ad esempio, di avere il  valore Test per utente **all'ora** nella finestra di dialogo Modifica combinazione di test per il test impostato su due utenti all'ora. Se la proprietà **Applica distribuzione a ritardo velocità** è impostata su **False**, non si prevede alcun intervallo di tolleranza nell'esecuzione dei test. Il test verrà eseguito ogni 30 minuti. In questo modo si è certi che verranno eseguiti 2 test all'ora.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Per specificare l'impostazione della proprietà Applica distribuzione a ritardo velocità per uno scenario

1. Aprire un test di carico.

   Viene visualizzato l'**Editor test di carico**. Verrà visualizzata la struttura ad albero del test di carico.

2. Nella cartella **Scenari** dell'albero del test di carico selezionare il nodo dello scenario a cui si vuole applicare la distribuzione della velocità.

3. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

   Le categorie e le proprietà dello scenario vengono visualizzate nella finestra **Proprietà**.

4. Come valore della proprietà **Applica distribuzione a ritardo velocità** selezionare **True** o **False**.

5. Selezionare **File**  >  **Salva.** È ora possibile eseguire il test di carico usando il nuovo valore di **Applica distribuzione a ritardo velocità**.

## <a name="see-also"></a>Vedi anche

- [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md)
- [Procedura dettagliata: Creare ed eseguire un test di carico](../test/walkthrough-create-and-run-a-load-test.md)
- [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)
