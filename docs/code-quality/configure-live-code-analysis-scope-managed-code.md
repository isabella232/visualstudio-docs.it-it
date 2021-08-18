---
title: Configurare l'ambito di analisi del codice in tempo reale per .NET
ms.date: 09/01/2020
description: Informazioni sull'analisi in background in Visual Studio. Informazioni su come limitare l'analisi al documento visibile, a tutti i documenti aperti o a tutti i file e i progetti.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 664d24c2732ee2c63475ac986fa9bbab78831493
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114186"
---
# <a name="configure-live-code-analysis-for-net"></a>Configurare l'analisi del codice in tempo reale per .NET

Visual Studio esegue una serie di analisi del codice in tempo reale, definite anche analisi in *background,* durante la modifica dei file di origine nell'editor. In parte è necessaria un'analisi minima per un'esperienza di modifica dell Visual Studio IDE accettabile. Alcuni di questi sono utili per migliorare la velocità di risposta per le funzionalità dell'IDE. Anche se in parte è necessario abilitare funzionalità IDE aggiuntive, ad esempio la diagnostica e le correzioni del codice dagli analizzatori Roslyn. In base alla funzionalità, queste analisi possono essere raggruppate nel modo seguente:

- **Calcolo in background della diagnostica:** analisi per calcolare errori, avvisi e suggerimenti nei file di origine. Queste informazioni di diagnostica vengono mostrate come voci nell'elenco degli errori e con una disarticola nell'editor. Possono essere classificati in due categorie:
  - Diagnostica del compilatore C# Visual Basic compilazione
  - Diagnostica dell'analizzatore Roslyn, che include:

    - Analizzatori IDE predefiniti per i suggerimenti di stile del codice
    - Analizzatori di CA predefiniti per i suggerimenti sulla qualità del codice
    - Pacchetti dell'analizzatore [di](./install-roslyn-analyzers.md) terze parti installati per i progetti nella soluzione corrente.

- **Altre analisi in background:** analisi per migliorare la velocità di risposta e Visual Studio'interazione per le funzionalità IDE. Di seguito sono riportati alcuni esempi di analisi di questo tipo:
  - Analisi in background dei file aperti.
  - Compilazione in background di progetti con file aperti per realizzare simboli per migliorare la velocità di risposta di determinate funzionalità IDE.
  - Compilazione di cache di sintassi e simboli.
  - Rilevamento dell'associazione della finestra di progettazione per i file di origine, ad esempio form, controlli e così via.

## <a name="default-analysis-scope"></a>Ambito di analisi predefinito

Per impostazione predefinita, l'analisi del codice in tempo reale per il calcolo in background della diagnostica viene eseguita per tutti i file aperti _in_ Visual Studio. Alcune delle _altre analisi in background indicate_ in precedenza vengono eseguite per tutti i progetti che hanno almeno un file aperto. Mentre alcune analisi in background vengono eseguite per l'intera soluzione.

## <a name="custom-analysis-scope"></a>Ambito di analisi personalizzato

L'ambito predefinito di ogni analisi in background è stato ottimizzato per l'esperienza utente, le funzionalità e le prestazioni ottimali per la maggior parte degli scenari e delle soluzioni dei clienti. In alcuni casi, tuttavia, i clienti possono scegliere di personalizzare questo ambito per ridurre o aumentare l'analisi in background. Esempio:

- Modalità risparmio energia: se gli utenti sono in esecuzione a batteria del portatile, è possibile che vogliano ridurre al minimo il consumo di energia per una durata maggiore della batteria. In questo scenario è necessario ridurre al minimo l'analisi in background.
- Analisi del codice su richiesta: se gli utenti preferiscono disattivare l'esecuzione dell'analizzatore in tempo reale ed eseguire manualmente l'analisi del codice su richiesta, è preferibile ridurre al minimo l'analisi in background. Vedere [Procedura: Eseguire manualmente l'analisi del codice su richiesta.](./how-to-run-code-analysis-manually-for-managed-code.md)
- Analisi completa della soluzione: se gli utenti vogliono visualizzare sempre tutta la diagnostica in tutti i file della soluzione, indipendentemente dal fatto che siano aperti o meno nell'editor. In questo scenario, è necessario ottimizzare l'ambito di analisi in background per l'intera soluzione.

A partire da Visual Studio 2019 versione 16.5, gli utenti possono personalizzare in modo esplicito l'ambito di tutte le analisi del codice in tempo reale, incluso il calcolo della diagnostica, per i progetti C# e Visual Basic. Gli ambiti di analisi disponibili sono:

- **Documento corrente:** riduce al minimo l'ambito di analisi del codice in tempo reale da eseguire solo per il file corrente o visibile nell'editor.
- **Documenti aperti:** ambito di analisi del codice attivo predefinito, come descritto nella sezione precedente.
- **Intera soluzione:** ottimizza l'ambito di analisi del codice in tempo reale da eseguire per tutti i file e i progetti nell'intera soluzione.

È possibile scegliere uno degli ambiti di analisi personalizzati precedenti nella finestra di dialogo Opzioni strumenti seguendo questa procedura:

1. Per aprire la **finestra di** dialogo Opzioni, sulla barra dei menu in Visual Studio **Strumenti**  >  **Opzioni**.

2. Nella finestra **di dialogo** Opzioni scegliere Editor **di testo**  >  **C#** o Avanzate **di**  >  **base.**

3. Selezionare l'ambito **di analisi in background desiderato** per personalizzare l'ambito di analisi. Al termine, scegliere **OK.**

![Ambito di analisi.](./media/background-analysis-scope.png)

> [!NOTE]
> Prima di Visual Studio 2019 versione 16.5, gli utenti possono personalizzare l'ambito  di analisi per il calcolo della diagnostica per l'intera soluzione usando la casella di controllo Abilita analisi completa della soluzione nella scheda Editor di testo Opzioni strumenti  >    >    >  **C#**   >   o Avanzate di base. Non è disponibile alcun supporto per ridurre al minimo l'ambito di analisi in background nelle versioni Visual Studio precedenti.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Ridurre automaticamente al minimo l'ambito di analisi del codice in tempo reale

Se Visual Studio rileva che sono disponibili almeno 200 MB di memoria di sistema, l'ambito di analisi del codice attivo viene ridotto automaticamente a "Documento corrente". In questo caso, viene visualizzato un avviso che informa che Visual Studio alcune funzionalità sono disabilitate. Un pulsante consente di tornare all'ambito di analisi precedente, se necessario.

![Testo dell'avviso che riduce al minimo l'ambito di analisi](./media/fsa_alert.png)

## <a name="see-also"></a>Vedi anche

- [Sospensione funzionalità automatica](./automatic-feature-suspension.md)
- [Richiesta di funzionalità della modalità risparmio energia](https://github.com/dotnet/roslyn/issues/38429)
