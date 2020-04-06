---
title: Informazioni sulle estensioni dei nomi di file Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03e07ec233ef975441a1f10507f0db872051558f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740353"
---
# <a name="about-file-name-extensions"></a>Informazioni sulle estensioni di file
Quando si registra un'estensione di file di un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage, si associa a una versione di . Questo è importante se più [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di una versione di è installata su un computer.

 Estensioni di file per VSPackage vengono registrati in **HKEY_CLASSES_ROOT** chiave con un valore predefinito che punta all'identificatore programmatico associato (ProgID).

 Nell'esempio seguente vengono illustrate le informazioni di registrazione per l'estensione di file *vcproj:*

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 I file [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] associati devono avere un ProgID con controllo delle versioni, ad `VisualStudio.vcproj.8.0`esempio . Un ProgID con controllo delle versioni consente alle installazioni side-by-side del prodotto di mantenere le associazioni di estensioni di file tra le versioni del prodotto. Un ProgID specifico della versione consente inoltre di utilizzare verbi standard, ad esempio open, edit e così via, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]senza la preoccupazione di sovrascrivere o essere sovrascritti da altre applicazioni o versioni di .

 In alcuni casi, il ProgID associato a un'estensione di file non deve essere modificato. Ad esempio, il ProgID per l'estensione del file *.htm* (progid - htmlfile) è hardcoded in diverse posizioni nel sistema operativo ed è ampiamente conosciuto e utilizzato in associazione con i file *.htm* e *.html.*

## <a name="see-also"></a>Vedere anche
- [Registrare le estensioni dei nomi di file per le distribuzioni side-by-sideRegister file name extensions for side-by-side deployments](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Specificare i gestori di file per le estensioni di fileSpecify file handlers for file name extensions](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
