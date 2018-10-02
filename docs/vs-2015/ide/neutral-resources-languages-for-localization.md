---
title: Lingue di risorse non associate ad alcun paese per la localizzazione | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a9470718743e506a7a8cd5ad03d9b6f69b1d5477
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518811"
---
# <a name="neutral-resources-languages-for-localization"></a>Linguaggi di risorse non associate ad alcun paese per la localizzazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La classe <xref:System.Resources.NeutralResourcesLanguageAttribute> specifica le impostazioni cultura delle risorse incluse nell'assembly principale. Questo attributo viene usato per migliorare le prestazioni facendo in modo che l'oggetto <xref:System.Resources.ResourceManager> non cerchi le risorse incluse nell'assembly principale.  
  
 Il codice seguente illustra come impostare la lingua di risorse neutra. Il codice può essere inserito in uno script di compilazione o nel file AssemblyInfo.vb o AssemblyInfo.cs.  
  
```vb  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```csharp  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Resources.ResourceManager>   
 [Introduzione alle applicazioni internazionali basate su .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Organizzazione gerarchica di risorse per la localizzazione](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Applicazioni localizzate](../ide/localizing-applications.md)   
 [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)

