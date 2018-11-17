---
title: Sulle estensioni di File | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 680f9e9f79430ea53da3566686b058c44894e494
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776083"
---
# <a name="about-file-name-extensions"></a>Informazioni sulle estensioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si registra un'estensione di file di un pacchetto VSPackage, è associarlo a una versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Questo è importante se più di una versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] viene installato in un computer.  
  
 Estensioni di file per i pacchetti VSPackage registrate nella chiave HKEY_CLASSES_ROOT con un valore predefinito che fa riferimento all'identificatore associato a livello di codice (ProgID).  
  
 Di seguito è riportato un esempio di informazioni di registrazione per l'estensione del file con estensione vcproj:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 File associati [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] deve avere un ProgID con controllo delle versioni, ad esempio `VisualStudio.vcproj.8.0`per consentire le installazioni side-by-side del prodotto per gestire le associazioni di estensione di file tra versioni del prodotto. Un ProgID specifico della versione consente inoltre di usare verbi standard, ad esempio open, modifica e così via, senza preoccuparsi della sovrascrittura o esserne sovrascritto da altre applicazioni o le versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 In alcuni casi, il ProgID associato a un'estensione di file non deve essere modificato. Ad esempio, il ProgID per l'estensione del file con estensione htm (progid = htmlfile) è hardcoded in un numero di posizioni nel sistema operativo ed è ampiamente noto e usate in associazione con file htm e HTML.  
  
## <a name="see-also"></a>Vedere anche  
 [La registrazione di estensioni di File per le distribuzioni Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Definizione dei gestori di file per le estensioni di file](../extensibility/specifying-file-handlers-for-file-name-extensions.md)

