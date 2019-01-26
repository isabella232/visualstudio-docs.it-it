---
title: Informazioni generali sugli strumenti di linguaggio specifico di dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 17a5908ddb6ecdd9f8434de1bd2792c4b86c989d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981987"
---
# <a name="overview-of-domain-specific-language-tools"></a>Informazioni generali sugli strumenti di linguaggio specifico di dominio
Domain-Specific Language Tools (strumenti DSL), che sono ospitati in Visual Studio, consentono di progettare un linguaggio specifico di dominio e quindi generare tutte le operazioni che gli utenti devono disporre per creare modelli basati sulla lingua.

 Gli strumenti seguenti sono inclusi negli strumenti DSL:

-   Creazione guidata progetto che usa i modelli di soluzioni differenti che consentono di iniziare a sviluppare il linguaggio specifico di dominio.

-   Finestra di progettazione con interfaccia grafica per la creazione e modifica la definizione di linguaggio specifico di dominio.

-   Un motore di convalida che consente di assicurarsi che la definizione del linguaggio specifico di dominio sia ben formata e consente di visualizzare errori e avvisi se si verificano problemi.

-   Un generatore di codice che richiede una definizione di linguaggio specifico di dominio come input e produce il codice sorgente come output.

## <a name="the-dsl-tools-solution"></a>La soluzione di strumenti DSL
 La procedura guidata finestra di progettazione Domain-Specific fornisce i modelli di soluzioni seguenti:

- Flusso di attività

- Diagrammi classi

- Linguaggio minimo

- Modelli di componenti

- WPF minimo

- Minimo Windows. Forms

- Libreria DSL

  Per altre informazioni, vedere [scelta di un modello di soluzione Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).

  La procedura guidata crea una soluzione di Visual Studio con i progetti seguenti:

- Dsl

   Progetto Dsl definisce il linguaggio specifico di dominio e dei relativi strumenti di modifica e di elaborazione.

- **DslPackage**

   Al progetto DslPackage determina la modalità di integrazione degli strumenti di linguaggio con Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>L'interfaccia grafica strumenti DSL
 È possibile usare l'interfaccia grafica strumenti DSL per aggiungere elementi e relazioni per il linguaggio specifico di dominio. Dopo aver aggiunto gli elementi, è possibile definire il proprio aspetto eseguendone il mapping alle forme, personalizzazione dei colori e aggiungendo gli elementi Decorator. È anche possibile aggiungere elementi alla casella degli strumenti.

## <a name="validation-in-dsl-tools"></a>Convalida in strumenti DSL
 Linguaggio specifico di dominio fornisce un livello di convalida per assicurarsi che il modello di dominio soddisfi i requisiti di base per la generazione di codice. In genere, quando si crea il proprio linguaggio specifico di dominio, è necessario aggiungere il proprio convalida per esprimere le regole per la logica di business. Per altre informazioni sulla convalida personalizzata, vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).

 È consigliabile convalidare il linguaggio specifico di dominio spesso quando si progettano. Se il linguaggio specifico di dominio presenta errori di convalida, è possibile generare codice sorgente. Viene eseguito il processo di generazione di codice sorgente dai modelli facendo **Trasforma tutti i modelli** sulla barra degli strumenti di Esplora soluzioni. Ogni volta che si modifica la definizione del linguaggio, assicurarsi anche di **Trasforma tutti i modelli**. Per altre informazioni, vedere [Procedura: Creare una soluzione Domain-Specific Language](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Personalizzazione degli strumenti DSL
 È possibile fornire codice aggiuntivo per perfezionare il comportamento del modello e per definire i vincoli per la lingua. Se necessario, è possibile apportare modifiche significative modificando i modelli di testo.

## <a name="distributing-your-dsl-solution"></a>Distribuzione della soluzione DSL
 Strumenti DSL genera un pacchetto che è ospitato in Visual Studio. Il pacchetto consente di visualizzare una casella degli strumenti DSL explorer e altri elementi dell'interfaccia utente che consentono agli utenti di creare modelli usando il linguaggio specifico di dominio.

 Quando si compila e si esegue la soluzione strumenti DSL in Visual Studio, una seconda istanza di Visual Studio viene illustrato l'aspetto del linguaggio specifico di dominio per l'utente del linguaggio. Dopo aver verificato che tutto funzioni correttamente, è possibile distribuire il `.vsix` file che si trovano nella cartella di compilazione del progetto DslPackage. Questo file è utilizzabile per installare il linguaggio DSL come un'estensione di Visual Studio in altri computer.  Per altre informazioni, vedere [distribuzione di soluzioni Domain-Specific Language](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Vedere anche

- [Istanza sperimentale](../extensibility/the-experimental-instance.md)
- [Glossario sugli strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)