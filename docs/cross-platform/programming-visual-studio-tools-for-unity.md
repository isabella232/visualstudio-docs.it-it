---
title: Programmazione di Visual Studio Tools per Unity | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 0811445e2dcf985aef7b6449ff3fb86c5ac9a1c8
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027374"
---
# <a name="program-visual-studio-tools-for-unity"></a>Programmazione di Visual Studio Tools per Unity
Questa sezione contiene esempi per l'uso dell'API di Visual Studio Tools per Unity.

## <a name="examples"></a>Esempi
 Ecco alcuni esempi che mostrano come è possibile usare le API di Visual Studio Tools per Unity.

### <a name="customize-project-files-created-by-vstu"></a>Personalizzare i file di progetto creati con VSTU
 Visual Studio Tools per Unity offre un callback in stile Unity durante la generazione dei file di progetto. Per informazioni su come è possibile modificare il file di progetto ogni volta che viene rigenerato, vedere [Esempio: Generazione dei file di progetto](../cross-platform/customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Condividere il callback di log di Unity con VSTU
 Visual Studio Tools per Unity registra un callback di log con Unity in modo da poter eseguire la console di Unity in Visual Studio. Se anche gli script di editor registrano un callback di log con Unity, il callback di VSTU potrebbe interferire con questo. Per informazioni su come è possibile condividere il callback di log di Unity con VSTU, vedere [Esempio: callback di log](../cross-platform/share-the-unity-log-callback-with-vstu.md).
