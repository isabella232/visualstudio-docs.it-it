---
title: Registrazione di estensioni di .NET Framework | Microsoft Docs
description: Informazioni su come aggiungere una cartella contenente un assembly che estende una versione specifica del .NET Framework al Registro di sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- dotnet
ms.openlocfilehash: 0af48178d270bcce0a83b81aa54fface2b0b1e3b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084831"
---
# <a name="register-extensions-of-the-net-framework"></a>Registrare estensioni di .NET Framework

È possibile sviluppare un assembly per estendere una versione specifica di .NET Framework. Per poter visualizzare l'assembly nella finestra di dialogo **Aggiungi riferimenti**, è necessario aggiungere la cartella che lo contiene al Registro di sistema.

 Si supponga, ad esempio, che la società Trey Research abbia sviluppato una libreria che estende .NET Framework 4 e voglia che gli assembly della libreria vengano visualizzati nella finestra di dialogo **Aggiungi riferimenti** quando un progetto ha come destinazione .NET Framework 4. Si supponga anche che si tratti di assembly a 32 bit in esecuzione su un computer a 32 bit o di assembly a 64 bit in esecuzione su un computer a 64 bit e che verranno installati nella cartella *C:\TreyResearch\Extensions4\\*.

 Registrare questa cartella usando la chiave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**. Assegnare alla chiave il valore predefinito **C:\TreyResearch\Extensions4**.

> [!NOTE]
> Il numero di build della versione di .NET Framework potrebbe essere diverso.

 Per registrare un assembly a 32 bit su un computer a 64 bit usare il nodo Wow6432, ad esempio: **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**.

### <a name="see-also"></a>Vedi anche

- [Visual Studio'integrazione](../msbuild/visual-studio-integration-msbuild.md)
