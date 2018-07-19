---
title: Sulle estensioni di File | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fd181bb7daca21ff263dcb7989a0aecbef3ed278
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081696"
---
# <a name="about-file-name-extensions"></a>Sulle estensioni di file
Quando si registra un'estensione di file di un pacchetto VSPackage, è associarlo a una versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Questo è importante se più di una versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene installato in un computer.  
  
 Estensioni di file per i pacchetti VSPackage registrate sotto **HKEY_CLASSES_ROOT** chiave con un valore predefinito che fa riferimento all'identificatore associato a livello di codice (ProgID).  
  
 L'esempio seguente mostra le informazioni di registrazione per il *VCPROJ* estensione file:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 File associati [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve avere un ProgID con controllo delle versioni, ad esempio `VisualStudio.vcproj.8.0`. Un ProgID con controllo delle versioni consente installazioni side-by-side del prodotto per gestire le associazioni di estensione di file tra versioni del prodotto. Un ProgID specifico della versione consente inoltre di usare verbi standard, ad esempio open, modifica e così via, senza preoccuparsi della sovrascrittura o esserne sovrascritto da altre applicazioni o le versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 In alcuni casi, il ProgID associato a un'estensione di file non deve essere modificato. Ad esempio, il ProgID per il *htm* estensione di file (progid = htmlfile) è hardcoded in un numero di posizioni nel sistema operativo, ed è ampiamente noto e usate in associazione con *htm* e*HTML* file.  
  
## <a name="see-also"></a>Vedere anche  
 [Registrare le estensioni di file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Specificare i gestori di file per le estensioni di file](../extensibility/specifying-file-handlers-for-file-name-extensions.md)