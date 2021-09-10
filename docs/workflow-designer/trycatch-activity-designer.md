---
title: Progettazione flussi di lavoro - ActivityDesigner TryCatch
description: Informazioni sull'attività TryCatch e su come usare l'ActivityDesigner TryCatch per creare e configurare un'attività TryCatch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 662bea4838b06843bc529cd41adc3e2bf33425ca
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963657"
---
# <a name="trycatch-activity-designer"></a>ActivityDesigner TryCatch

**L'ActivityDesigner TryCatch** viene usato per creare e configurare <xref:System.Activities.Statements.TryCatch> un'attività.

## <a name="the-trycatch-activity"></a>Attività TryCatch
 <xref:System.Activities.Statements.TryCatch>L'attività contiene <xref:System.Activities.Statements.TryCatch.Try%2A> un'attività , una raccolta **di Catch \<TException>** e un'attività <xref:System.Activities.Statements.TryCatch.Finally%2A> . Un <xref:System.Activities.Statements.Catch%601> oggetto di tipo **TException** contiene un <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> oggetto e un oggetto <xref:System.Activities.Statements.Catch%601.Action%2A> . che vengono usate insieme per implementare un meccanismo tipico di gestione degli errori basato sulle eccezioni. Un'attività <xref:System.Activities.Statements.TryCatch> tenta di eseguire la relativa attività <xref:System.Activities.Statements.TryCatch.Try%2A>. Se <xref:System.Activities.Statements.TryCatch.Try%2A> l'attività genera un'eccezione, l'attività usa la <xref:System.Activities.Statements.TryCatch> **raccolta Catch<TException \>** per trovare la corrispondenza con l'eccezione. Se è presente una corrispondenza, viene eseguito il del corrispondente <xref:System.Activities.Statements.Catch%601.Action%2A> **catch, \<TException>** fungendo da logica di gestione degli errori per l'eccezione. Se le attività nella sezione di <xref:System.Activities.Statements.TryCatch.Try%2A> o le attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> terminano in modo corretto, l'attività di <xref:System.Activities.Statements.TryCatch> esegue la relativa attività di <xref:System.Activities.Statements.TryCatch.Finally%2A>. Per altre informazioni, vedere [Eccezioni Windows flusso di lavoro.](/dotnet/framework/windows-workflow-foundation/exceptions)

### <a name="using-the-trycatch-activity-designer"></a>Utilizzo dell'ActivityDesigner TryCatch

Accedere **all'ActivityDesigner TryCatch** nella **categoria Gestione errori** della Casella degli **strumenti**.

**L'ActivityDesigner TryCatch** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie Progettazione flussi di lavoro ogni volta che vengono in genere inserite attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . In questo modo viene creata un'attività <xref:System.Activities.Statements.TryCatch> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito TryCatch. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **TryCatch** o nella **casella DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nell'area dell'ActivityDesigner **TryCatch.**

Fare clic sul pulsante di espansione nell'angolo superiore destro della finestra di progettazione **TryCatch** per visualizzare le caselle **Try**(Prova), **Catches**(Intercetta) e **Finally** (Infine) nella visualizzazione espansa. Per aggiungere un catch, fare clic **sul pulsante Add new catch (Aggiungi nuovo catch)** nella finestra di progettazione **TryCatch.** Il pulsante diventa una casella combinata del tipo. Selezionare un tipo di eccezione e premere INVIO per aggiungere il catch. Dopo aver aggiunto **un catch**, l'area catch si espande e un'attività può essere rilasciata nel catch per definire la logica di esecuzione per il catch. Si noti la presenza di una casella di testo a destra dell'area dei catch espansa. Questa casella consente di assegnare un nome alla variabile dell'eccezione. La variabile di eccezione può essere usata solo per le attività all'interno dello stesso **catch.**

La **finestra di progettazione TryCatch** non supporta la modifica di **Catch.** Se si vuole modificare il tipo di eccezione, è necessario eliminare **catch** e aggiungerne uno nuovo. Un **catch** può essere eliminato selezionandolo ed  eliminandolo oppure scegliendo Elimina dal menu di scelta rapida a cui si accede facendo clic con il pulsante destro del mouse.

### <a name="the-trycatch-properties"></a>Proprietà di TryCatch

Nella tabella seguente vengono illustrate <xref:System.Activities.Statements.TryCatch> le proprietà e viene descritto come vengono utilizzate nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.TryCatch>. Il percorso predefinito è TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|Falso|L'attività è stata eseguita per prima quando viene eseguito <xref:System.Activities.Statements.TryCatch>.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|Falso|Raccolta di elementi **Catch** da controllare quando l'attività <xref:System.Activities.Statements.TryCatch.Try%2A> genera un'eccezione.<br /><br /> È necessario aggiungere almeno un'attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> o un'attività nel blocco <xref:System.Activities.Statements.TryCatch.Finally%2A>.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|Falso|L'attività da eseguire quando <xref:System.Activities.Statements.TryCatch.Try%2A> e qualsiasi attività necessaria nella raccolta <xref:System.Activities.Statements.TryCatch.Catches%2A> completano l'esecuzione.<br /><br /> È necessario aggiungere almeno un'attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> o un'attività nel blocco <xref:System.Activities.Statements.TryCatch.Finally%2A>.|

## <a name="see-also"></a>Vedi anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Gettare](../workflow-designer/throw-activity-designer.md)
