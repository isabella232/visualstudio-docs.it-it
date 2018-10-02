---
title: Salvataggio dei dati | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataRow.RowState
- DataSet.GetChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- DBDirect methods
- updating data
- data [Visual Studio], saving
- TableAdapter DBDirect methods
- databases, updating
- TableAdapter.Update method
- data [Visual Studio], updating
- saving data
- updating databases
ms.assetid: 21d2b115-62e4-4ac9-a873-dcbb535b8af8
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 14ff0e62608c3e2ab0c72366d9544f1d1309737a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532378"
---
# <a name="saving-data"></a>Salvataggio di dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Salvataggio dei dati è che il processo di persistenza modificato i dati nel modello di dati di un'applicazione all'archivio dati originale, in genere un database relazionale, ad esempio SQL Server.  
  
 L'aggiornamento di un'origine dati mediante un modello di dati è in genere un processo in due passaggi. Il primo passaggio consiste nell'aggiornare il modello di dati con nuove informazioni, ovvero nuovi record, record modificati o eliminati i record. Il secondo passaggio consiste nel salvare le modifiche nel modello di dati nel database.  
  
 Gli argomenti seguenti descrivono i concetti e attività associate di salvataggio dei dati.  
  
## <a name="related-topics"></a>Argomenti correlati  
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)  
 Fornisce una panoramica del modo in cui vengono apportate modifiche in un set di dati e come il set di dati tiene traccia delle informazioni sulle modifiche per salvare le modifiche a un database.  
  
 [Salvataggio di dati di entità](../data-tools/saving-entity-data.md)  
 Viene descritto come salvare le modifiche nel [ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205) e [WCF Data Services 4.5](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) applicazioni.