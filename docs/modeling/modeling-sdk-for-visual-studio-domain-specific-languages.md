---
title: SDK di modellazione per Visual Studio (linguaggi specifici di dominio)
titleSuffix: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9524e071edc82ba2da78df77afdda85e0ac10505
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860335"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>SDK di modellazione per Visual Studio (linguaggi specifici di dominio)

Usando il SDK di modellazione per Visual Studio, è possibile creare strumenti di sviluppo avanzato basato su modello che è possibile integrare in Visual Studio. Analogamente, è possibile creare una o più definizioni di modello e integrarle in un set di strumenti.

MSDK è basato sulla definizione di un modello creato per rappresentare i concetti nella propria area aziendale. È possibile racchiudere il modello con un'ampia gamma di strumenti, ad esempio una vista basata su diagramma, la possibilità di generare codice e altri artefatti, i comandi per trasformare il modello e la possibilità di interagire con il codice e altri oggetti in Visual Studio. Quando si sviluppa il modello, è possibile combinarlo con altri modelli e strumenti per formare un potente set di strumenti avanzati incentrati sulla propria attività di sviluppo.

MSDK consente di compilare rapidamente un modello nel formato di linguaggio specifico di dominio (DSL). Iniziare utilizzando un editor specifico per definire uno schema o una sintassi astratta insieme a una notazione grafica. Utilizzando questa definizione, VMSDK genera:

- Implementazione di modello con un'API fortemente tipizzata eseguita in un archivio basato sulle transazioni.

- Finestra di esplorazione ad albero.

- Editor grafico in cui gli utenti possono visualizzare il modello o parti definite.

- Metodi di serializzazione che salvano i modelli in XML leggibile.

- Funzionalità per generare codice di programma e altri elementi utilizzando il modello di testo.

Tutte queste funzionalità possono essere personalizzate ed estese. Le estensioni sono integrate in modo che sia comunque possibile aggiornare la definizione DSL e rigenerare le funzionalità senza perdere le estensioni.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[Post di blog correlati](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

Per indicazioni sulla risoluzione dei problemi e alle tecniche più avanzate, visitare [forum di estendibilità degli strumenti di modellazione e DSL di Visual Studio](http://go.microsoft.com/fwlink/?LinkID=186074).

## <a name="in-this-section"></a>In questa sezione
 [Introduzione ai linguaggi specifici del dominio](../modeling/getting-started-with-domain-specific-languages.md)

 [Informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md)

 [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)

 [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)

 [Convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md)

 [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)

 [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)

 [Informazioni sul codice DSL](../modeling/understanding-the-dsl-code.md)

 [Personalizzazione dell'archiviazione dei file e della serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md)

 [Distribuzione di soluzioni per un linguaggio specifico di dominio](../modeling/deploying-domain-specific-language-solutions.md)

 [Creazione di un linguaggio specifico di dominio basato su Windows Form](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

 [Creazione di un linguaggio specifico di dominio basato su WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

 [Procedura: Estendere la finestra di progettazione Domain-Specific Language](../modeling/how-to-extend-the-domain-specific-language-designer.md)

 [Edizioni di Visual Studio supportate per l'SDK di visualizzazione e modellazione](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)

 [Procedura: Eseguire la migrazione di un linguaggio specifico di dominio a una nuova versione](../modeling/how-to-migrate-a-domain-specific-language-to-a-new-version.md)

 [Riferimento API per SDK di modellazione per Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
