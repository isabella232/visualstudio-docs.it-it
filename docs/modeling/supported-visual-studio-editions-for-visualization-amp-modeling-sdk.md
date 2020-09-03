---
title: Edizioni di Visual Studio supportate per l'SDK di visualizzazione e modellazione
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3be233ce8730879c2f0406ec9cc180685992c6bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544937"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Edizioni di Visual Studio supportate per l'SDK di visualizzazione e modellazione

Di seguito sono elencati gli elenchi delle edizioni di Visual Studio supportate con [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] negli ambienti di creazione e distribuzione. Per ulteriori informazioni su queste edizioni, vedere il [centro per sviluppatori](https://visualstudio.microsoft.com/)Microsoft Visual Studio.

## <a name="authoring-edition"></a>Edizione per lo sviluppo

Per definire un linguaggio specifico di dominio (Domain-Specific Language, DSL) devono essere installati i componenti seguenti:

|Prodotto|Collegamento di download|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|SDK di visualizzazione e modellazione di Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Edizioni per la distribuzione

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] supporta le seguenti configurazioni per la distribuzione dei linguaggi specifici del dominio compilati:

- Visual Studio Enterprise

- Visual Studio Professional

- Pacchetto ridistribuibile Visual Studio Shell (modalità integrata)

- Pacchetto ridistribuibile Visual Studio Shell (modalità isolata)

> [!NOTE]
> Per consentire l'esecuzione di un linguaggio DSL in un prodotto shell, è necessario impostare il campo **supported vs Edition** nel manifesto dell'estensione. Per altre informazioni, vedere [Distribuzione di soluzioni per un linguaggio specifico di dominio](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
