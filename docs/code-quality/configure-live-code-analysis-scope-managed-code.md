---
title: Configurare l'ambito di analisi del codice in tempo reale per .NET
ms.date: 09/01/2020
description: Scopri di più sull'analisi in background in Visual Studio. Vedere come limitare l'analisi al documento visibile, a tutti i documenti aperti o a tutti i file e progetti.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9690e50ccbe927702ef1b3e7e99545c07cdced41
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348463"
---
# <a name="configure-live-code-analysis-for-net"></a>Configurare l'analisi del codice in tempo reale per .NET

Visual Studio esegue una serie di analisi del codice in tempo reale, denominate anche *analisi in background* , mentre si modificano i file di origine nell'editor. Alcune di esse sono richieste di analisi minime per un'esperienza di modifica accettabile dell'IDE di Visual Studio. Alcune di queste funzionalità sono per migliorare la velocità di risposta per le funzionalità IDE. Sebbene alcune di queste funzioni consentano di abilitare funzionalità aggiuntive dell'IDE, ad esempio la diagnostica e le correzioni del codice degli analizzatori Roslyn. In base alla funzionalità, queste analisi possono essere raggruppate come segue:

- **Calcolo in background della diagnostica** : analisi per calcolare errori, avvisi e suggerimenti nei file di origine. Questi dati di diagnostica vengono visualizzati come voci nell'elenco errori e come controllo ortografia durante nell'editor. Possono essere classificati in due categorie:
  - Diagnostica del compilatore C# e Visual Basic
  - Diagnostica di Roslyn Analyzer, che include:

    - Analizzatori IDE predefiniti per i suggerimenti di stile del codice
    - Analizzatori CA predefiniti per i suggerimenti sulla qualità del codice
    - Pacchetti dell'analizzatore di terze parti [installati](./install-roslyn-analyzers.md) per i progetti nella soluzione corrente.

- **Altre analisi in background** : analisi per migliorare la velocità di risposta e l'interazione di Visual Studio per le funzionalità IDE. Di seguito sono riportati alcuni esempi di analisi di questo tipo:
  - Analisi in background dei file aperti.
  - Compilazione in background dei progetti con file aperti per realizzare i simboli per migliorare la velocità di risposta di alcune funzionalità IDE.
  - Compilazione della sintassi e delle cache di simboli.
  - Rilevamento dell'associazione della finestra di progettazione per i file di origine, ad esempio form, controlli e così via.

## <a name="default-analysis-scope"></a>Ambito di analisi predefinito

Per impostazione predefinita, l'analisi del codice in tempo reale per il calcolo in background della diagnostica viene eseguita per tutti i file _aperti_ in Visual Studio. Alcune delle _altre analisi in background_ indicate sopra vengono eseguite per tutti i progetti, che hanno almeno un file aperto. Sebbene vengano eseguite alcune analisi in background per l'intera soluzione.

## <a name="custom-analysis-scope"></a>Ambito di analisi personalizzato

L'ambito predefinito di ogni analisi in background è stato ottimizzato per l'esperienza utente, le funzionalità e le prestazioni ottimali per la maggior parte degli scenari e delle soluzioni dei clienti. In alcuni casi, tuttavia, i clienti potrebbero voler personalizzare questo ambito per ridurre o aumentare l'analisi in background. Ad esempio:

- Modalità risparmio energia: se gli utenti eseguono la batteria portatile, è possibile che vogliano ridurre al minimo il consumo di energia elettrica per una durata maggiore della batteria. In questo scenario, è consigliabile ridurre al minimo l'analisi in background.
- Analisi del codice su richiesta: se gli utenti preferiscono disattivare l'esecuzione di Live Analyzer e eseguire manualmente l'analisi del codice su richiesta, è necessario ridurre al minimo l'analisi in background. Vedere [procedura: eseguire manualmente l'analisi del codice su richiesta](./how-to-run-code-analysis-manually-for-managed-code.md).
- Analisi completa della soluzione: se gli utenti vogliono visualizzare sempre tutti i dati di diagnostica in tutti i file della soluzione, indipendentemente dal fatto che siano aperti o meno nell'editor. In questo scenario, è opportuno ottimizzare l'ambito dell'analisi in background per l'intera soluzione.

A partire da Visual Studio 2019 versione 16,5, gli utenti possono personalizzare in modo esplicito l'ambito di tutte le analisi del codice in tempo reale, incluso il calcolo della diagnostica, per i progetti C# e Visual Basic. Gli ambiti di analisi disponibili sono:

- **Documento corrente** : riduce al minimo l'ambito dell'analisi del codice in tempo reale per l'esecuzione solo per il file corrente o visibile nell'editor.
- **Documenti aperti** : ambito predefinito dell'analisi del codice in tempo reale, come descritto nella sezione precedente.
- **Intera soluzione** : ingrandisce l'ambito dell'analisi del codice in tempo reale da eseguire per tutti i file e i progetti nell'intera soluzione.

È possibile scegliere uno degli ambiti di analisi personalizzati sopra indicati nella finestra di dialogo Opzioni strumenti attenendosi alla procedura seguente:

1. Per aprire la finestra di dialogo **Opzioni** , sulla barra dei menu in Visual Studio scegliere **strumenti**  >  **Opzioni**.

2. Nella finestra di dialogo **Opzioni** scegliere **editor di testo**  >  **C#** o **Basic**  >  **Advanced**.

3. Consente di selezionare l' **ambito di analisi in background** desiderato per personalizzare l'ambito di analisi. Al termine, scegliere **OK** .

![Ambito di analisi.](./media/background-analysis-scope.png)

> [!NOTE]
> Prima di Visual Studio 2019 versione 16,5, gli utenti possono personalizzare l'ambito di analisi per il calcolo della diagnostica nell'intera soluzione usando la casella di controllo **Abilita analisi della soluzione completa** da **strumenti**  >  **Opzioni**  >  **editor di testo**  >  **C#** o **Basic**  >  scheda **Avanzate** di base. Non è disponibile alcun supporto per ridurre al minimo l'ambito di analisi in background nelle versioni precedenti di Visual Studio.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Riduci automaticamente l'ambito di analisi del codice in tempo reale

Se Visual Studio rileva che sono disponibili 200 MB o meno di memoria di sistema, l'ambito dell'analisi del codice in tempo reale verrà automaticamente ridotto a "documento corrente". In tal caso, viene visualizzato un avviso che informa che Visual Studio ha disabilitato alcune funzionalità. Un pulsante consente di tornare all'ambito di analisi precedente, se necessario.

![Testo dell'avviso per la riduzione dell'ambito dell'analisi](./media/fsa_alert.png)

## <a name="see-also"></a>Vedere anche

- [Sospensione funzionalità automatica](./automatic-feature-suspension.md)
- [Richiesta di funzionalità della modalità di risparmio energia](https://github.com/dotnet/roslyn/issues/38429)
