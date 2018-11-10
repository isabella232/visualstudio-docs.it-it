---
title: Creazione di stringhe di filtro per Progettazione tabelle | Microsoft Docs
description: Creazione di stringhe di filtro per Progettazione tabelle
author: ghogen
manager: douge
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: ff8c3dd927e81b9e131242a9a6631a8297046a6e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002871"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>Creazione di stringhe di filtro per Progettazione tabelle
## <a name="overview"></a>Panoramica
Per filtrare i dati in una tabella di Azure che viene visualizzato in Visual Studio **Progettazione tabelle**, si costruisce una stringa di filtro e immetterla nel campo del filtro. La sintassi della stringa di filtro è definita da WCF Data Services ed è simile a una clausola SQL WHERE, ma viene inviata al servizio tabella tramite una richiesta HTTP. Il **Progettazione tabelle** gestisce la codifica appropriata, in modo per filtrare un valore della proprietà desiderata, è necessario immettere solo il nome della proprietà, operatore di confronto, valore dei criteri e, facoltativamente, valore booleano operatore nel campo del filtro. Non è necessario includere l'opzione di query $filter come si farebbe quando si costruisce un URL per eseguire una query sulla tabella usando il [riferimento all'API REST di servizi di archiviazione](http://go.microsoft.com/fwlink/p/?LinkId=400447).

WCF Data Services si basano le [Open Data Protocol](http://go.microsoft.com/fwlink/p/?LinkId=214805) (OData). Per informazioni dettagliate sull'opzione di query di sistema filter (**$filter**), vedere la [specifica sulle convenzioni URI OData](http://go.microsoft.com/fwlink/p/?LinkId=214806).

## <a name="comparison-operators"></a>Operatori di confronto
Gli operatori logici seguenti sono supportati per tutti i tipi di proprietà:

| Operatore logico | Descrizione | Stringa di filtro di esempio |
| --- | --- | --- |
| eq |Uguale |Città eq "Redmond" |
| gt |Maggiore di |Prezzo gt 20 |
| Ge |Maggiore o uguale a |Prezzo ge 10 |
| lt |Minore di |Prezzo lt 20 |
| le |Minore o uguale a |Prezzo le 100 |
| ne |Non uguaglianza |Città ne "Londra" |
| e |E |Prezzo le 200 and prezzo gt 3,5 |
| oppure |Or |Prezzo le 3,5 or prezzo gt 200 |
| not |non |non isAvailable |

Quando si crea una stringa di filtro, le regole seguenti sono importanti:

* Usare gli operatori logici per confrontare una proprietà con un valore. Si noti che non è possibile confrontare una proprietà su un valore dinamico. un lato dell'espressione deve essere una costante.
* Tutte le parti della stringa di filtro sono tra maiuscole e minuscole.
* Il valore della costante deve essere dello stesso tipo di dati come proprietà in ordine per il filtro restituisca risultati validi. Per altre informazioni sui tipi di proprietà supportati, vedere [informazioni sul modello di dati del servizio tabella](http://go.microsoft.com/fwlink/p/?LinkId=400448).

## <a name="filtering-on-string-properties"></a>Applicazione di filtri alle proprietà della stringa
Quando si filtra le proprietà della stringa, includere la costante di stringa tra virgolette singole.

Nell'esempio seguente vengono applicati filtri al **PartitionKey** e **RowKey** proprietà; non chiave aggiuntive sono anche possibile aggiungere proprietà alla stringa di filtro:

    PartitionKey eq 'Partition1' and RowKey eq '00001'

È possibile racchiudere ogni espressione di filtro tra parentesi, anche se non è necessario:

    (PartitionKey eq 'Partition1') and (RowKey eq '00001')

Si noti che il servizio tabelle non supporta le query con caratteri jolly e non sono supportati sia in Progettazione tabelle. Tuttavia, è possibile eseguire prefisso corrispondente usando gli operatori di confronto sul prefisso desiderato. L'esempio seguente restituisce le entità con una proprietà LastName che inizia con la lettera "A":

    LastName ge 'A' and LastName lt 'B'

## <a name="filtering-on-numeric-properties"></a>Applicazione di filtri alle proprietà numeriche
Per filtrare un numero intero o un numero a virgola mobile, specificare il numero senza virgolette.

Questo esempio restituisce tutte le entità con una proprietà Age il cui valore è maggiore di 30:

    Age gt 30

Questo esempio restituisce tutte le entità con una proprietà amountdue il cui valore è minore o uguale a 100,25:

    AmountDue le 100.25

## <a name="filtering-on-boolean-properties"></a>Applicazione di filtri alle proprietà booleane
Per filtrare un valore booleano, specificare **true** oppure **false** senza virgolette.

L'esempio seguente restituisce tutte le entità in cui la proprietà IsActive è impostata **true**:

    IsActive eq true

È anche possibile scrivere questa espressione di filtro senza l'operatore logico. Nell'esempio seguente, il servizio tabelle restituirà anche tutte le entità in cui IsActive è **true**:

    IsActive

Per restituire tutte le entità in cui IsActive è false, è possibile usare not operatore:

    not IsActive

## <a name="filtering-on-datetime-properties"></a>Applicazione di filtri alle proprietà DateTime
Per filtrare un valore DateTime, specificare il **datetime** (parola chiave), seguita dalla costante data/ora tra virgolette singole. La costante data/ora deve essere in formato UTC combinato, come descritto in [formattazione di valori della proprietà DateTime](http://go.microsoft.com/fwlink/p/?LinkId=400449).

L'esempio seguente restituisce le entità in cui la proprietà CustomerSince è uguale a 10 luglio 2008:

    CustomerSince eq datetime'2008-07-10T00:00:00Z'
