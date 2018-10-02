---
title: Registrazione di estensioni di .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a2d3e281562be5234e0a70a877a6c169c346995
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519889"
---
# <a name="registering-extensions-of-the-net-framework"></a>Registrazione di estensioni di .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [la registrazione di estensioni di .NET Framework](https://docs.microsoft.com/visualstudio/msbuild/registering-extensions-of-the-dotnet-framework).  
  
  
È possibile sviluppare un assembly per estendere una versione specifica di .NET Framework. Per poter visualizzare l'assembly nella finestra di dialogo **Aggiungi riferimenti**, è necessario aggiungere la cartella che lo contiene al Registro di sistema.  
  
 Si supponga, ad esempio, che la società Trey Research abbia sviluppato una libreria che estende .NET Framework 4 e voglia che gli assembly della libreria vengano visualizzati nella finestra di dialogo **Aggiungi riferimenti** quando un progetto ha come destinazione .NET Framework 4. Si supponga anche che si tratti di assembly a 32 bit in esecuzione su un computer a 32 bit o di assembly a 64 bit in esecuzione su un computer a 64 bit e che verranno installati nella cartella C:\TreyResearch\Extensions4\.  
  
 Registrare questa cartella usando la chiave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\. Assegnare alla chiave il valore predefinito C:\TreyResearch\Extensions4.  
  
> [!NOTE]
>  Il numero di build della versione di .NET Framework potrebbe essere diverso.  
  
 Per registrare un assembly a 32 bit su un computer a 64 bit, usare il nodo Wow6432, ad esempio: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\.  
  
## <a name="see-also"></a>Vedere anche  
 [Integrazione con Visual Studio](../msbuild/visual-studio-integration-msbuild.md)



