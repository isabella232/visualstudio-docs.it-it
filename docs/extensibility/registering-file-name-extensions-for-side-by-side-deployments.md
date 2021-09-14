---
title: Registrare le estensioni dei nomi file per gli ID side-by-side
description: Informazioni sulla registrazione delle estensioni di file per le distribuzioni side-by-side, che consente agli utenti di aprire i file nella versione appropriata di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: be7c5c2a45d42840c41b5860596cc4fd8c883bf0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626009"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Registrare le estensioni di file per le distribuzioni side-by-side
Per i pacchetti VSPackage distribuiti in un ambiente side-by-side, è necessario registrare le estensioni di file per associare i file alla versione corretta di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . A meno che non si usi un'estensione di file specifica della versione, la registrazione consente agli utenti di aprire i file di progetto e di elemento di progetto nella versione appropriata di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Contenuto della sezione
- [Informazioni sulle estensioni di file](../extensibility/about-file-name-extensions.md) Viene illustrata la modalità di registrazione delle estensioni di file.

- [Specificare i gestori di file per le estensioni di file](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Fornisce informazioni su come registrare le applicazioni che possono aprire, modificare e così via, una determinata estensione di file.

- [Registrare i verbi per le estensioni di file](../extensibility/registering-verbs-for-file-name-extensions.md) Viene illustrato come registrare i verbi.

- [Gestire le associazioni di file side-by-side](../extensibility/managing-side-by-side-file-associations.md) Viene illustrato come gestire le installazioni side-by-side in cui una determinata versione di deve essere richiamata [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per aprire un file.

## <a name="related-sections"></a>Sezioni correlate
- [Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Vengono descritti i problemi relativi a più versioni di e al pacchetto VSPackage durante lo sviluppo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e la distribuzione agli utenti finali.
