---
title: Metadati MSBuild elementi | Microsoft Docs
description: Informazioni sui metadati facoltativi degli elementi che hanno un significato per alcuni SDK o destinazioni di MSBuild, ma non sono impostati per impostazione predefinita per ogni elemento.
ms.custom: SEO-VS-2020
ms.date: 07/13/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- msbuild, common item metadata
- item metadata (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: f4a893a516d8c9237e2dd4ebf06812fcbcd02de9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055083"
---
# <a name="common-msbuild-item-metadata"></a>Metadati dell'elemento MSBuild comuni

La tabella seguente descrive i metadati facoltativi degli elementi che hanno significato per alcuni SDK o destinazioni di MSBuild, ma che non sono impostati per impostazione predefinita per ogni elemento. È possibile impostarli per influenzare il comportamento di compilazione, ma solo se l'SDK o i file di destinazione in uso lo riconoscono.

| Metadati degli elementi | SDK | Descrizione |
|---------------| ------- | -------------|
|%(Collegamento)| Tutti |Il Visual Studio del progetto usa metadati (se presenti) per modificare ciò che viene visualizzato nell'albero del progetto. È possibile inserire un file in una struttura di cartelle logica diversa `Link` **in Esplora soluzioni**.<br />L'attività esamina anche per determinare la posizione nella directory di output in cui copiare un file, se si tratta di uno degli `AssignTargetPath` `Link` elementi copiati.|
|%(LinkBase)| .NET Core SDK | Consente di impostare la cartella da utilizzare per i `Link` metadati per i gruppi di elementi. |

## <a name="see-also"></a>Vedi anche

- [Proprietà di progetto MSBuild comuni](../msbuild/common-msbuild-project-properties.md)
- [Elementi di progetto MSBuild comuni](../msbuild/common-msbuild-project-items.md)
- [Metadati noti degli elementi di MSBuild](msbuild-well-known-item-metadata.md)