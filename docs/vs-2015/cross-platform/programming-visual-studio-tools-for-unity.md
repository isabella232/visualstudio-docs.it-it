---
title: Programmazione di Visual Studio Tools per Unity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
caps.latest.revision: 5
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: 469478f05546a32bb890f759d3d00cb447b54d2b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654048"
---
# <a name="programming-visual-studio-tools-for-unity"></a>Programmazione di Visual Studio Tools per Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa sezione contiene esempi per l'uso dell'API di Visual Studio Tools per Unity.  
  
## <a name="examples"></a>Esempi  
 Ecco alcuni esempi che mostrano come è possibile usare le API di Visual Studio Tools per Unity.  
  
### <a name="customize-project-files-created-by-vstu"></a>Personalizzare i file di progetto creati con VSTU  
 Visual Studio Tools per Unity offre un callback in stile Unity durante la generazione dei file di progetto. Per informazioni su come è possibile modificare il file di progetto ogni volta che viene rigenerato, vedere [Esempio: Generazione dei File di progetto](../cross-platform/customize-project-files-created-by-vstu.md).  
  
### <a name="share-the-unity-log-callback-with-vstu"></a>Condividere il callback di log di Unity con VSTU  
 Visual Studio Tools per Unity registra un callback di log con Unity in modo da poter eseguire la console di Unity in Visual Studio. Se anche gli script di editor registrano un callback di log con Unity, il callback di VSTU potrebbe interferire con questo. Per informazioni su come è possibile condividere il callback di log di Unity con VSTU, vedere [Esempio: Callback di log](../cross-platform/share-the-unity-log-callback-with-vstu.md).
