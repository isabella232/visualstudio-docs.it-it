---
title: Informazioni generali sugli strumenti di linguaggio specifico di dominio
description: Informazioni sul modo in cui gli strumenti DSL consentono di progettare un linguaggio specifico di dominio e quindi generare tutto ciò che gli utenti devono avere per creare modelli basati sul linguaggio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e88a6157e5c9db7914ac6f7470d793be11dfdfc8
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362028"
---
# <a name="overview-of-domain-specific-language-tools"></a>Informazioni generali sugli strumenti di linguaggio specifico di dominio
Gli strumenti di linguaggio Domain-Specific (strumenti DSL), ospitati in Visual Studio, consentono di progettare un linguaggio specifico di dominio e di generare tutti gli elementi necessari agli utenti per creare modelli basati sul linguaggio.

 In Strumenti DSL sono inclusi gli strumenti seguenti:

- Una procedura guidata di creazione di progetti che usa modelli di soluzioni diverse per facilitare l'avvio dello sviluppo di un linguaggio specifico di dominio.

- Una finestra di progettazione con interfaccia grafica per la creazione e la modifica della definizione del linguaggio specifico di dominio.

- Un motore di convalida che assicura che la definizione del linguaggio specifico di dominio sia ben formata e visualizza errori e avvisi in caso di problemi.

- Un generatore di codice che riceve la definizione di un linguaggio specifico di dominio come input e produce codice sorgente come output.

## <a name="the-dsl-tools-solution"></a>Soluzione Strumenti DSL
 La Creazione guidata Finestra di progettazione Domain-Specific Language offre i modelli di soluzione seguenti:

- Flusso di attività

- Diagrammi classi

- Linguaggio minimo

- Modelli componente

- WPF minimo

- Windows.Forms minimo

- Libreria DSL

  Per altre informazioni, vedere [Scelta di un modello di soluzione per un linguaggio specifico di dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).

  La procedura guidata crea una soluzione di Visual Studio che include i progetti seguenti:

- Dsl

   Il progetto Dsl definisce il linguaggio specifico di dominio e i relativi strumenti di modifica e di elaborazione.

- **DslPackage**

   Il progetto DslPackage determina il modo in cui gli strumenti di linguaggio si integrano con Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>Interfaccia grafica di Strumenti DSL
 È possibile usare l'interfaccia grafica di Strumenti DSL per aggiungere elementi e relazioni al linguaggio specifico di dominio. Dopo aver aggiunto gli elementi, è possibile definirne l'aspetto eseguendone il mapping alle forme, personalizzandone i colori e aggiungendo elementi Decorator. È anche possibile aggiungere elementi alla casella degli strumenti.

## <a name="validation-in-dsl-tools"></a>Convalida in Strumenti DSL
 DSL è dotato di un livello di convalida che verifica che il modello di dominio soddisfi i requisiti di base per la generazione di codice. Quando si crea un linguaggio specifico di dominio personalizzato, in genere si aggiunge una convalida personalizzata che esprima le regole della logica di business. Per altre informazioni sulla convalida personalizzata, vedere [Convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).

 È consigliabile convalidare spesso il linguaggio specifico di dominio durante la progettazione. Se il linguaggio specifico di dominio presenta errori di convalida, non è possibile generare codice sorgente. È possibile eseguire il processo di generazione di codice sorgente dai modelli facendo clic su **Trasforma tutti i modelli** sulla barra degli strumenti di Esplora soluzioni. Ogni volta che si modifica la definizione del linguaggio, assicurarsi anche di **trasformare tutti i modelli**. Per altre informazioni, vedere [procedura: creare una soluzione di linguaggio Domain-Specific](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Personalizzazione di Strumenti DSL
 È possibile offrire codice aggiuntivo per perfezionare il comportamento del modello e definire vincoli per il linguaggio. Se necessario, è possibile apportare modifiche significative modificando i modelli di testo.

## <a name="distributing-your-dsl-solution"></a>Distribuzione della soluzione DSL
 Gli strumenti DSL generano un pacchetto ospitato in Visual Studio. Il pacchetto visualizza una casella degli strumenti, la finestra di esplorazione DSL e altri elementi dell'interfaccia utente che consentono agli utenti di creare modelli usando il linguaggio specifico di dominio creato.

 Quando si compila ed esegue la soluzione strumenti DSL in Visual Studio, una seconda istanza di Visual Studio Mostra il modo in cui il linguaggio specifico di dominio esamina l'utente della lingua. Dopo aver verificato che tutto funzioni correttamente, è possibile distribuire il file `.vsix` disponibile nella cartella di compilazione del progetto DslPackage. Questo file può essere usato per installare il linguaggio DSL come estensione di Visual Studio in altri computer.  Per altre informazioni, vedere [Distribuzione di soluzioni per un linguaggio specifico di dominio](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Vedi anche

- [Istanza sperimentale](../extensibility/the-experimental-instance.md)
- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))