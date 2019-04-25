---
title: Modelli per progetti e file
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30a20e5810d5c361fddf8cd934863fcb1186b5d0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62793452"
---
# <a name="project-and-item-templates"></a>Modelli di progetti e di elementi

I modelli di progetti e di elementi offrono stub riutilizzabili con codice e strutture di base che gli utenti possono personalizzare in base alle esigenze.

## <a name="visual-studio-templates"></a>modelli di Visual Studio

Con Visual Studio vengono installati vari modelli di progetti e di elementi predefiniti. Questi modelli, ad esempio i modelli **Applicazione Web ASP.NET** e **Libreria di classi**, sono disponibili per la scelta quando si crea un nuovo progetto. I modelli di elemento, ad esempio file di codice, file XML, pagine HTML e fogli di stile, sono visualizzati nella finestra **Aggiungi nuovo elemento**.

I modelli rappresentano un punto di partenza per iniziare a creare progetti o per espandere i progetti esistenti. I modelli di progetto forniscono i file necessari per un determinato tipo di progetto, includono i riferimenti ad assembly standard e impostano le proprietà di progetto predefinite e le opzioni del compilatore. La complessità dei modelli di elementi può variare: da un singolo file vuoto con una determinata estensione di file fino a più file del codice sorgente con codice stub, file di informazioni sulla progettazione e risorse incorporate.

È possibile usare modelli installati, creare modelli personalizzati o scaricare e usare modelli creati dalla community. Per altre informazioni, vedere [Procedura: Creare modelli di progetto](../ide/how-to-create-project-templates.md) e [Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Contenuto di un modello

Tutti i modelli di progetti e di elementi, sia quelli installati con Visual Studio, sia quelli creati dall'utente, funzionano in base agli stessi principi e hanno contenuti simili. Tutti i modelli contengono gli elementi seguenti:

- I file da creare quando viene usato il modello, tra cui i file del codice sorgente, le risorse incorporate, i file di progetto e così via.

::: moniker range="vs-2017"

- Un file con estensione *vstemplate*, che contiene i metadati necessari per creare un progetto o un elemento dal modello e per visualizzare il modello nelle finestre **Nuovo progetto** e **Aggiungi nuovo elemento**.

::: moniker-end

::: moniker range=">=vs-2019"

- Un file con estensione *vstemplate*, che contiene i metadati necessari per creare un progetto o un elemento dal modello e per visualizzare il modello nella pagina **Crea un nuovo progetto** o nella finestra di dialogo **Aggiungi nuovo elemento**.

::: moniker-end

   Per altre informazioni sui file con estensione *vstemplate*, vedere [Parametri di modello](../ide/template-parameters.md).

Quando questi file vengono compressi in un file con estensione *zip* e inseriti nella cartella corretta, Visual Studio li visualizza automaticamente nelle seguenti posizioni:

::: moniker range="vs-2017"

- I modelli di progetto vengono visualizzati nella finestra **Nuovo progetto**.

::: moniker-end

::: moniker range=">=vs-2019"

- I modelli di progetto vengono visualizzati nella pagina **Crea un nuovo progetto**.

::: moniker-end

- I modelli di elementi vengono visualizzati nella finestra **Aggiungi nuovo elemento**.

Per altre informazioni sulle cartelle dei modelli, vedere [Procedura: Individuare e organizzare modelli](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare modelli di progetto](../ide/how-to-create-project-templates.md)
- [Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md)
- [Parametri di modello](../ide/template-parameters.md)
- [Personalizzare i modelli](../ide/customizing-project-and-item-templates.md)
- [Pacchetti NuGet nei modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)