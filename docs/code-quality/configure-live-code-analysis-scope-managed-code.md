---
title: Configurare l'ambito di analisi del codice attivo per il codice gestitoConfigure live code analysis scope for managed code
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 300e3f276a45cfe2115311c7d27eedce365616cf
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432238"
---
# <a name="how-to-configure-live-code-analysis-scope-for-managed-code"></a>Procedura: configurare l'ambito di analisi del codice attivo per il codice gestitoHow to: Configure live code analysis scope for managed code

## <a name="what-is-live-code-analysis-for-managed-code"></a>Che cos'è "Analisi del codice in tempo reale" per il codice gestito?
Visual Studio esegue una serie di analisi del codice in tempo reale, definite anche analisi in *background*, durante la modifica dei file di origine nell'editor. Alcune di essa è necessaria un'analisi minima per un'esperienza di modifica IDE di Visual Studio accettabile. Alcuni di essi è per una migliore velocità di risposta per le funzionalità IDE. Mentre alcuni di essi è quello di abilitare funzionalità IDE aggiuntive, ad esempio la diagnostica e correzioni di codice da analizzatori Roslyn.While some of it is to enable additional IDE functionality, such as diagnostics and code fixes from Roslyn analyzers. In base alla funzionalità, queste analisi possono essere raggruppate come segue:

- **Calcolo in background della diagnostica:** analisi per calcolare errori, avvisi e suggerimenti nei file di origine. Questi dati di diagnostica vengono visualizzati come voci nell'elenco degli errori e come scarabocchi nell'editor. Possono essere classificati in due categorie:
    - Diagnostica del compilatore C e Visual Basic
    - Diagnostica analizzatore Roslyn, che include:

        - Analizzatori IDE incorporati per suggerimenti di stile di codice e
        - Pacchetti analizzatori di terze parti [installati](./install-roslyn-analyzers.md) per i progetti nella soluzione corrente.

- Altre analisi di **base:** analisi per migliorare la velocità di risposta e l'interazione di Visual Studio per le funzionalità IDE. Alcuni esempi di tali analisi sono:
    - Analisi in background dei file aperti.
    - Compilazione in background di progetti con file aperti per realizzare simboli per una migliore velocità di risposta di alcune funzionalità IDE.
    - Compilazione di cache di sintassi e simboli.
    - Rilevamento dell'associazione della finestra di progettazione per i file di origine, ad esempio moduli, controlli e così via.

## <a name="default-analysis-scope"></a>Ambito di analisi predefinito

Per impostazione predefinita, l'analisi del codice attivo per il calcolo in background della diagnostica viene eseguita per tutti i file aperti in Visual Studio.By default, live code analysis for background computation of diagnostics executes for all the files that are _opened_ in Visual Studio. Poche delle _altre analisi_ di base di cui sopra vengono eseguite per tutti i progetti, che hanno almeno un file aperto. Mentre poche analisi in background vengono eseguite per l'intera soluzione.

## <a name="custom-analysis-scope"></a>Ambito di analisi personalizzato

L'ambito predefinito di ogni analisi in background è stato regolato per l'esperienza utente ottimale, funzionalità e prestazioni per la maggior parte degli scenari e delle soluzioni dei clienti. Tuttavia, in alcuni casi i clienti potrebbero voler personalizzare questo ambito per ridurre o aumentare l'analisi in background. Ad esempio:

- Modalità risparmio energia: se gli utenti sono in esecuzione con la batteria del computer portatile, potrebbero voler ridurre al minimo il consumo di energia per una maggiore durata della batteria. In questo scenario, si desidera ridurre al minimo l'analisi in background.
- Analisi del codice su richiesta: se gli utenti preferiscono disattivare l'esecuzione dell'analizzatore in tempo reale e l'esecuzione manuale dell'analisi del codice su richiesta, si desidera ridurre al minimo l'analisi in background. Vedere [Procedura: eseguire manualmente l'analisi](./how-to-run-code-analysis-manually-for-managed-code.md)del codice su richiesta .
- Analisi completa della soluzione: se gli utenti desiderano visualizzare sempre tutta la diagnostica in tutti i file della soluzione, indipendentemente dal fatto che siano aperti o meno nell'editor. In questo scenario, vorrebbero massimizzare l'ambito di analisi in background per l'intera soluzione.

A partire da Visual Studio 2019 versione 16.5, gli utenti possono personalizzare in modo esplicito l'ambito di tutte le analisi del codice in tempo reale, incluso il calcolo della diagnostica, per i progetti di Visual Basic e di Visual Basic. Gli ambiti di analisi disponibili sono:

- **Documento corrente**: Riduce al minimo l'ambito di analisi del codice attivo da eseguire solo per il file corrente o visibile nell'editor.
- **Documenti aperti**: Ambito predefinito di analisi del codice in tempo reale, come descritto nella sezione precedente.
- **Intera soluzione**: Massimizza l'ambito di analisi del codice in tempo reale da eseguire per tutti i file e i progetti nell'intera soluzione.

È possibile scegliere uno degli ambiti di analisi personalizzati sopra indicati nella finestra di dialogo Opzioni degli strumenti attenendosi alla procedura seguente:

1. Per aprire la finestra di dialogo **Opzioni,** sulla barra dei menu di Visual Studio scegliere**Opzioni** **strumenti** > .

2. Nella finestra di dialogo **Opzioni,** scegliere **Editor di** > testo**in C,** o**Avanzate**di **base** > .

3. Selezionare **l'ambito** di analisi di sfondo desiderato per personalizzare l'ambito di analisi. Al termine, scegliere **OK.**

![Ambito di analisi.](./media/background-analysis-scope.png)

> [!NOTE]
> Prima di Visual Studio 2019 versione 16.5, gli utenti possono personalizzare l'ambito di analisi per il calcolo della diagnostica in tutta la soluzione usando la casella di controllo Abilita**Options** > **Text Editor** > analisi completa **Basic** > della **soluzione** **dalla** > **scheda** C **.** Non è disponibile alcun supporto per ridurre al minimo l'ambito di analisi in background nelle versioni precedenti di Visual Studio.There is no support to minimize the background analysis scope in prior Visual Studio versions.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Ridurre automaticamente al minimo l'ambito dell'analisi del codice in tempo realeAutomatically minimize live code analysis

Se Visual Studio rileva che sono disponibili 200 MB o meno di memoria di sistema, riduce automaticamente l'ambito dell'analisi del codice attivo a "Documento corrente". In questo caso, viene visualizzato un avviso che informa che Visual Studio ha disabilitato alcune funzionalità. Un pulsante consente di tornare all'ambito di analisi precedente, se lo si desidera.

![Testo dell'avviso riducendo al minimo l'ambito di analisi](./media/fsa_alert.png)

## <a name="see-also"></a>Vedere anche

- [Sospensione funzionalità automatica](./automatic-feature-suspension.md)
- [Richiesta di funzionalità della modalità risparmio energia](https://github.com/dotnet/roslyn/issues/38429)
