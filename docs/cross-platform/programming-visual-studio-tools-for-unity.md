---
title: Programmazione di Visual Studio Tools per Unity | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
caps.latest.revision: "3"
author: conceptdev
ms.author: crdun
manager: crdun
ms.openlocfilehash: 7d099fae62e808f2a86db53241fc7e774c5ae945
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/29/2017
---
# <a name="programming-visual-studio-tools-for-unity"></a>Programmazione di Visual Studio Tools per Unity
Questa sezione contiene esempi per l'uso dell'API di Visual Studio Tools per Unity.  

## <a name="examples"></a>Esempi  
 Ecco alcuni esempi che mostrano come è possibile usare le API di Visual Studio Tools per Unity.  

### <a name="customize-project-files-created-by-vstu"></a>Personalizzare i file di progetto creati con VSTU  
 Visual Studio Tools per Unity offre un callback in stile Unity durante la generazione dei file di progetto. Per informazioni su come è possibile modificare il file di progetto ogni volta che viene rigenerato, vedere [Esempio: generazione di file di progetto](../cross-platform/customize-project-files-created-by-vstu.md).  

### <a name="share-the-unity-log-callback-with-vstu"></a>Condividere il callback di log di Unity con VSTU  
 Visual Studio Tools per Unity registra un callback di log con Unity in modo da poter eseguire la console di Unity in Visual Studio. Se anche gli script di editor registrano un callback di log con Unity, il callback di VSTU potrebbe interferire con questo. Per informazioni su come è possibile condividere il callback di log di Unity con VSTU, vedere [Esempio: callback di log](../cross-platform/share-the-unity-log-callback-with-vstu.md).
