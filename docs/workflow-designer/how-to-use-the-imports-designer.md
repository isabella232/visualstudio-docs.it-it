---
title: 'Progettazione flussi di lavoro - Procedura: Usare Progettazione importazioni'
description: Informazioni su come progettazione importazioni consente di immettere spazi dei nomi per i tipi che verranno utilizzati nelle espressioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 2a7ca00f988981dd7a5d1e6c0e2954ba27441499
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135322"
---
# <a name="how-to-use-the-imports-designer"></a>Procedura: utilizzare la finestra di progettazione importazioni

La finestra di progettazione importazioni consente di immettere gli spazi dei nomi per i tipi usati nelle espressioni. Analogamente alle parole chiave **Imports** o **using** in Visual Basic e C#, la specifica di spazi dei nomi nella finestra di progettazione delle importazioni consente di immettere semplicemente un nome di tipo nell'espressione anziché un nome completo del tipo di versione.

Sulla finestra di progettazione importazioni influiscono sia le modifiche all'interfaccia utente che quelle eseguite quando viene salvato il flusso di lavoro. Quando viene salvato il flusso di lavoro, alla finestra di progettazione importazioni è possibile aggiungere automaticamente spazi dei nomi, tra cui:

- Spazi dei nomi per qualsiasi tipo usato nelle dichiarazioni di variabili e argomenti.

- Spazi dei nomi per qualsiasi tipo usato nelle espressioni.

- Qualsiasi altro spazio dei nomi necessario per la serializzazione del flusso di lavoro (ad esempio, gli spazi dei nomi usati da attività personalizzate rilasciate nel flusso di lavoro).

  Quando viene salvato il flusso di lavoro, è possibile notare che alcuni spazi dei nomi eliminati manualmente sono stati aggiunti di nuovo automaticamente alla finestra di progettazione importazioni a causa della logica descritta nell'elenco precedente.

## <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Per aggiungere uno spazio dei nomi all'elenco degli spazi dei nomi importati

1. Aprire un'applicazione del servizio flusso di lavoro WCF, un'applicazione console del flusso di lavoro o un progetto di libreria di attività Visual Studio o un'applicazione del flusso di lavoro rihosted.

2. Fare **clic su** Importazioni nella parte inferiore dell'area di disegno principale. Verrà visualizzata la finestra di progettazione importazioni.

3. Immettere o selezionare uno spazio dei nomi dal controllo dell'elenco a discesa nella parte superiore della finestra di progettazione importazioni.

     Mentre si digita, viene visualizzato un elenco degli spazi dei nomi validi che corrispondono ai caratteri tipizzati.

4. Premere **INVIO** per aggiungere lo spazio dei nomi all'elenco.

5. Se si vuole rimuovere uno spazio dei nomi dall'elenco, selezionare lo spazio dei nomi e quindi premere **CANC** sulla tastiera. Si noti che è possibile eliminare uno spazio dei nomi solo se non è valido per qualsiasi motivo, ad esempio se il progetto non fa più riferimento all'assembly che lo contiene.
