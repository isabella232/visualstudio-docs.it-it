---
title: Programmazione di Visual Studio Tools per Unity | Microsoft Docs
description: Vedere esempi di programmazione con l'API Visual Studio Tools per Unity (VSTU). Personalizzare i file di progetto creati con VSTU. Condividere il callback di log di Unity con VSTU.
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
ms.openlocfilehash: 0372cfd110df77867a683b27b17f92cd70ba75aa
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039885"
---
# <a name="program-visual-studio-tools-for-unity"></a>Programmazione di Visual Studio Tools per Unity
Questa sezione contiene esempi per l'uso dell'API di Visual Studio Tools per Unity.

## <a name="examples"></a>Esempi
 Ecco alcuni esempi che mostrano come è possibile usare le API di Visual Studio Tools per Unity.

### <a name="customize-project-files-created-by-vstu"></a>Personalizzare i file di progetto creati con VSTU
 Visual Studio Tools per Unity offre un callback in stile Unity durante la generazione dei file di progetto. Per informazioni su come è possibile modificare il file di progetto ogni volta che viene rigenerato, vedere [esempio: generazione di file di progetto](../cross-platform/customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Condividere il callback di log di Unity con VSTU
 Visual Studio Tools per Unity registra un callback di log con Unity in modo da poter eseguire la console di Unity in Visual Studio. Se anche gli script di editor registrano un callback di log con Unity, il callback di VSTU potrebbe interferire con questo. Per informazioni su come è possibile condividere il callback di log di Unity con VSTU, vedere [esempio: callback di log](../cross-platform/share-the-unity-log-callback-with-vstu.md).
