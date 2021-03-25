---
title: Informazioni sulle estensioni di file | Microsoft Docs
description: Informazioni su come registrare le estensioni dei nomi di file per i pacchetti VSPackage e associarle a una versione specifica di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f38bee1b62340f7d557ac2e5190fc5c48d9268fe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060146"
---
# <a name="about-file-name-extensions"></a>Informazioni sulle estensioni di file
Quando si registra un'estensione di file di un pacchetto VSPackage, questo viene associato a una versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Questo è importante se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in un computer è installata più di una versione di.

 Le estensioni di file per i pacchetti VSPackage sono registrate in **HKEY_CLASSES_ROOT** chiave con un valore predefinito che punta all'identificatore a livello di codice (ProgID) associato.

 Nell'esempio seguente vengono illustrate le informazioni di registrazione per l'estensione di file *. vcproj* :

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 I file associati a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] devono avere un ProgID con versione, ad esempio `VisualStudio.vcproj.8.0` . Un ProgID con versione consente installazioni affiancate del prodotto per mantenere le associazioni dell'estensione di file tra le versioni del prodotto. Un ProgID specifico della versione consente anche di usare verbi standard, ad esempio Open, Edit e così via, senza dover sovrascrivere o essere sovrascritti da altre applicazioni o versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 In alcuni casi, il ProgID associato a un'estensione di file non deve essere modificato. Il ProgID per l'estensione di file *htm* (ProgID = htmlfile), ad esempio, è hardcoded in numerose posizioni del sistema operativo ed è ampiamente noto e utilizzato in associazione ai file con estensione *htm* e *HTML* .

## <a name="see-also"></a>Vedi anche
- [Registrare le estensioni di file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Specificare i gestori di file per le estensioni di file](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
