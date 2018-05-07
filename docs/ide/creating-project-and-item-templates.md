---
title: Modelli di Visual Studio per progetti e file | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 900b750df391029a1bed15b2da003f94c085148a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="project-and-item-templates"></a>Modelli di progetti e di elementi

I modelli di progetti e di elementi offrono stub riutilizzabili con codice e strutture di base che gli utenti possono personalizzare in base alle esigenze.

## <a name="visual-studio-templates"></a>modelli di Visual Studio

Con Visual Studio vengono installati vari modelli di progetti e di elementi predefiniti. Ad esempio, i modelli **App Windows Forms** e **Libreria di classi** di Visual Basic e C# visualizzati nella finestra di dialogo **Nuovo progetto** sono esempi di modelli di progetti. I modelli di elementi sono visualizzati nella finestra di dialogo **Aggiungi nuovo elemento** e comprendono elementi come file di codice, file XML, pagine HTML e fogli di stile.

I modelli rappresentano un punto di partenza per iniziare a creare progetti o per espandere i progetti esistenti. I modelli di progetto forniscono i file necessari per un determinato tipo di progetto, includono i riferimenti ad assembly standard e impostano le proprietà di progetto predefinite e le opzioni del compilatore. La complessità dei modelli di elementi può variare: da un singolo file vuoto con una determinata estensione di file fino a più file del codice sorgente con codice stub, file di informazioni sulla progettazione e risorse incorporate.

È possibile usare i modelli installati disponibili nelle finestre di dialogo **Nuovo progetto** e **Aggiungi nuovo elemento**, creare modelli personalizzati o scaricare e usare modelli creati dalla community. Per altre informazioni, vedere [Procedura: Creare modelli di progetto](../ide/how-to-create-project-templates.md) e [Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Contenuto di un modello

Tutti i modelli di progetti e di elementi, sia quelli installati con Visual Studio, sia quelli creati dall'utente, funzionano in base agli stessi principi e hanno contenuti simili. Tutti i modelli contengono gli elementi seguenti:

- I file da creare quando viene usato il modello, tra cui i file del codice sorgente, le risorse incorporate, i file di progetto e così via.

- Un file con estensione *vstemplate* contiene i metadati necessari per visualizzare il modello nelle finestre di dialogo **Nuovo progetto** e **Aggiungi nuovo elemento** e per creare un progetto o un elemento dal modello. Per altre informazioni sui file con estensione *vstemplate*, vedere [Parametri di modello](../ide/template-parameters.md).

Quando questi file vengono compressi in un file con estensione *zip* e inseriti nella cartella corretta, Visual Studio li visualizza automaticamente nelle seguenti posizioni:

- I modelli di progetti vengono visualizzati nella finestra di dialogo **Nuovo progetto**.

- I modelli di elementi vengono visualizzati nella finestra di dialogo **Aggiungi nuovo elemento**.

Per altre informazioni sulle cartelle dei modelli, vedere [Procedura: Individuare e organizzare modelli](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="starter-kits"></a>Starter kit

Gli starter kit sono modelli avanzati che possono essere condivisi con altri membri della community. Uno starter kit include esempi di codice compilabili, documentazione e altre risorse per facilitare l'apprendimento di nuovi strumenti e tecniche di programmazione durante la compilazione di applicazioni utili e reali. I contenuti e le procedure di base per gli starter kit sono identici a quelli dei modelli. Per altre informazioni, vedere [Procedura: Creare starter kit](../ide/how-to-create-starter-kits.md).

## <a name="see-also"></a>Vedere anche

[Procedura: Creare modelli di progetto](../ide/how-to-create-project-templates.md)  
[Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md)  
[Parametri di modello](../ide/template-parameters.md)  
[Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)  
[Pacchetti NuGet nei modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)