---
title: Edizioni Visual Studio supportate per Visualization and Modeling SDK
description: Informazioni sulle edizioni Visual Studio supportate con gli strumenti DSL negli ambienti di creazione e distribuzione.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8435f37ebe68e954af135be0f513247191ea8a9
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386397"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Edizioni di Visual Studio supportate per l'SDK di visualizzazione e modellazione

Di seguito sono elencati gli Visual Studio edizioni supportate con [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] negli ambienti di creazione e distribuzione. Per altre informazioni su queste edizioni, vedere il Microsoft Visual Studio [Developer Center.](https://visualstudio.microsoft.com/)

## <a name="authoring-edition"></a>Edizione per lo sviluppo

Per definire un linguaggio specifico di dominio (Domain-Specific Language, DSL) devono essere installati i componenti seguenti:

|Prodotto|Collegamento di download|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true)|
|SDK di visualizzazione e modellazione di Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Edizioni per la distribuzione

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] supporta le configurazioni seguenti per la distribuzione dei linguaggi specifici di dominio compilati:

- Visual Studio Enterprise

- Visual Studio Professional

- Pacchetto ridistribuibile Visual Studio Shell (modalità integrata)

- Pacchetto ridistribuibile Visual Studio Shell (modalità isolata)

> [!NOTE]
> Per fare in modo che un DSL possa essere eseguito in un prodotto shell, è necessario impostare il **campo Supported VS Edition** (Edizione di Visual Studio supportata) nel manifesto dell'estensione. Per altre informazioni, vedere [Distribuzione di soluzioni per un linguaggio specifico di dominio](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))