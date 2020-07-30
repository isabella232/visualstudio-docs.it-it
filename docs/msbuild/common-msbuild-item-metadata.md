---
title: Metadati dell'elemento MSBuild comuni | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c715c16782733a08bb617a464c1aa9510d35b54
ms.sourcegitcommit: dda98068c0f62ccd1a19fdfde4bdb822428d0125
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2020
ms.locfileid: "87425957"
---
# <a name="common-msbuild-item-metadata"></a>Metadati dell'elemento MSBuild comuni

La tabella seguente descrive i metadati facoltativi degli elementi che hanno un significato per alcuni SDK o destinazioni di MSBuild, ma che non sono impostati per impostazione predefinita per ogni elemento. È possibile impostarle in modo da influenzare il comportamento della compilazione, ma solo se i file SDK o di destinazione in uso lo riconoscono.

| Metadati degli elementi | SDK | Descrizione |
|---------------| ------- | -------------|
|% (Collegamento)| Tutti |Il sistema di progetto di Visual Studio USA i `Link` metadati (se presenti) per modificare gli elementi visualizzati nell'albero del progetto. è possibile inserire un file in una struttura di cartelle logica diversa in **Esplora soluzioni**.<br />Inoltre, l' `AssignTargetPath` attività esamina `Link` per determinare la posizione della directory di output in cui copiare un file, se si tratta di uno degli elementi che vengono copiati.|
|% (Collegamento)| .NET Core SDK | Utilizzato per impostare la cartella da utilizzare per i `Link` metadati per i gruppi di elementi. |

## <a name="see-also"></a>Vedere anche

- [Proprietà di progetto MSBuild comuni](../msbuild/common-msbuild-project-properties.md)
- [Elementi di progetto MSBuild comuni](../msbuild/common-msbuild-project-items.md)
- [Metadati noti degli elementi di MSBuild](msbuild-well-known-item-metadata.md)