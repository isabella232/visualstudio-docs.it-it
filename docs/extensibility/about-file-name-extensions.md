---
title: Informazioni sulle estensioni di file | Microsoft Docs
description: Informazioni su come registrare le estensioni di file per i pacchetti VSPackage e associarle a una versione specifica di Visual Studio.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 75629d0f559db2dac717d44eb3dc59b23c8af9e0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127792"
---
# <a name="about-file-name-extensions"></a>Informazioni sulle estensioni di file
Quando si registra un'estensione di file di un VSPackage, è necessario associarlo a una versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Questo è importante se in un computer sono installate più [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versioni di .

 Le estensioni di file per VSPackage vengono registrate HKEY_CLASSES_ROOT **chiave** con un valore predefinito che punta all'identificatore programmatico (ProgID) associato.

 L'esempio seguente mostra le informazioni di registrazione per l'estensione di file *vcproj:*

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 I file associati a devono avere un ProgID con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] controllo delle versioni, ad esempio `VisualStudio.vcproj.8.0` . Un ProgID con controllo delle versioni consente alle installazioni side-by-side del prodotto di mantenere le associazioni delle estensioni di file tra le versioni del prodotto. Un ProgID specifico della versione consente anche di usare verbi standard, ad esempio open, edit e così via, senza il problema di sovrascrivere o essere sovrascritto da altre applicazioni o versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 In alcuni casi, il ProgID associato a un'estensione di file non deve essere modificato. Ad esempio, progID per l'estensione di file *.htm* (progid = htmlfile) è hard-coded in diverse posizioni nel sistema operativo ed è ampiamente noto e usato in associazione con *i* file.htm *e.html.*

## <a name="see-also"></a>Vedi anche
- [Registrare le estensioni di file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Specificare i gestori di file per le estensioni di file](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
