---
title: Registrazione di estensioni di .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18df04fc706ea716f7c22baa6508930f0f94a6f6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54801466"
---
# <a name="registering-extensions-of-the-net-framework"></a>Registrazione di estensioni di .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
È possibile sviluppare un assembly per estendere una versione specifica di .NET Framework. Per poter visualizzare l'assembly nella finestra di dialogo **Aggiungi riferimenti**, è necessario aggiungere la cartella che lo contiene al Registro di sistema.  
  
 Si supponga, ad esempio, che la società Trey Research abbia sviluppato una libreria che estende .NET Framework 4 e voglia che gli assembly della libreria vengano visualizzati nella finestra di dialogo **Aggiungi riferimenti** quando un progetto ha come destinazione .NET Framework 4. Si supponga anche che si tratti di assembly a 32 bit in esecuzione su un computer a 32 bit o di assembly a 64 bit in esecuzione su un computer a 64 bit e che verranno installati nella cartella C:\TreyResearch\Extensions4\.  
  
 Registrare questa cartella usando la chiave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\. Assegnare alla chiave il valore predefinito C:\TreyResearch\Extensions4.  
  
> [!NOTE]
>  Il numero di build della versione di .NET Framework potrebbe essere diverso.  
  
 Per registrare un assembly a 32 bit su un computer a 64 bit, usare il nodo Wow6432, ad esempio: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\.  
  
## <a name="see-also"></a>Vedere anche  
 [Integrazione con Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
