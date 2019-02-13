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
ms.openlocfilehash: ccdc91643725e8799f587d14923ecf7620fc13b3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774374"
---
# <a name="programming-visual-studio-tools-for-unity"></a>Programmazione di Visual Studio Tools per Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Questa sezione contiene esempi per l'uso dell'API di Visual Studio Tools per Unity.  
  
## <a name="examples"></a>Esempi  
 Ecco alcuni esempi che mostrano come è possibile usare le API di Visual Studio Tools per Unity.  
  
### <a name="customize-project-files-created-by-vstu"></a>Personalizzare i file di progetto creati con VSTU  
 Visual Studio Tools per Unity offre un callback in stile Unity durante la generazione dei file di progetto. Per informazioni su come è possibile modificare il file di progetto ogni volta che viene rigenerato, vedere [Esempio: generazione di file di progetto](../cross-platform/customize-project-files-created-by-vstu.md).  
  
### <a name="share-the-unity-log-callback-with-vstu"></a>Condividere il callback di log di Unity con VSTU  
 Visual Studio Tools per Unity registra un callback di log con Unity in modo da poter eseguire la console di Unity in Visual Studio. Se anche gli script di editor registrano un callback di log con Unity, il callback di VSTU potrebbe interferire con questo. Per informazioni su come è possibile condividere il callback di log di Unity con VSTU, vedere [Esempio: callback di log](../cross-platform/share-the-unity-log-callback-with-vstu.md).
