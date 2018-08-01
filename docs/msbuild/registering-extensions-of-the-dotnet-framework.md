---
title: Registrazione di estensioni di .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 0017255b67042a7e42b54325b24512a295ebeaf5
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180152"
---
# <a name="register-extensions-of-the-net-framework"></a>Registrare estensioni di .NET Framework
È possibile sviluppare un assembly per estendere una versione specifica di .NET Framework. Per poter visualizzare l'assembly nella finestra di dialogo **Aggiungi riferimenti**, è necessario aggiungere la cartella che lo contiene al Registro di sistema.  
  
 Si supponga, ad esempio, che la società Trey Research abbia sviluppato una libreria che estende .NET Framework 4 e voglia che gli assembly della libreria vengano visualizzati nella finestra di dialogo **Aggiungi riferimenti** quando un progetto ha come destinazione .NET Framework 4. Si supponga anche che si tratti di assembly a 32 bit in esecuzione su un computer a 32 bit o di assembly a 64 bit in esecuzione su un computer a 64 bit e che verranno installati nella cartella *C:\TreyResearch\Extensions4\\*.  
  
 Registrare questa cartella usando la chiave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**. Assegnare alla chiave il valore predefinito **C:\TreyResearch\Extensions4**.  
  
> [!NOTE]
>  Il numero di build della versione di .NET Framework potrebbe essere diverso.  
  
 Per registrare un assembly a 32 bit su un computer a 64 bit usare il nodo Wow6432, ad esempio: **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**.  
  
### <a name="see-also"></a>Vedere anche  
 [Integrazione con Visual Studio](../msbuild/visual-studio-integration-msbuild.md)