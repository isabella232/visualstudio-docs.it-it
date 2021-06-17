---
title: Gestire progetti di applicazioni Python
description: I progetti in Visual Studio gestiscono le dipendenze tra i file e la complessità delle relazioni in un'applicazione.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c9a20ea3baee84657e26e2d98bb5726c20ceba9e
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254901"
---
# <a name="python-projects-in-visual-studio"></a>Progetti Python in Visual Studio

Per definire le applicazioni Python, si usano in genere solo file e cartelle, ma questa struttura può diventare complessa se le dimensioni delle applicazioni aumentano e interessano magari anche file generati automaticamente, JavaScript per le applicazioni Web e così via. Un progetto di Visual Studio aiuta a gestire questa complessità. Il progetto, un file con estensione *pyproj*, identifica tutti i file di origine e di contenuto associati al progetto, contiene le informazioni di compilazione relative a ogni file, gestisce le informazioni per l'integrazione con sistemi di controllo del codice sorgente e consente di organizzare l'applicazione in componenti logici.

![Progetto Python in Esplora soluzioni](media/projects-solution-explorer.png)

I progetti vengono inoltre sempre gestiti all'interno di una *soluzione* Visual Studio, che può contenere un numero qualsiasi di progetti che fanno riferimento l'uno all'altro. Ad esempio, un progetto di Python può fare riferimento a un progetto C++ che implementa un modulo di estensione. Con questa relazione, Visual Studio genera automaticamente il progetto C++ (se necessario) quando si avvia il debug del progetto di Python. Per informazioni di carattere generale, vedere [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).

In Visual Studio è disponibile un'ampia gamma di modelli di progetto Python per configurare rapidamente numerose strutture di applicazione, incluso un modello per creare un progetto da un albero delle cartelle esistente e un modello per creare un progetto pulito e vuoto. Per un indice, vedere [Modelli di progetto](#project-templates).

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019 supporta l'apertura di una cartella contenente codice Python e l'esecuzione del codice senza creare file di progetto e soluzione di Visual Studio. Per altre informazioni, vedere [Avvio rapido: Aprire ed eseguire codice Python in una cartella](quickstart-05-python-visual-studio-open-folder.md). L'uso di un file di progetto offre tuttavia alcuni vantaggi, come illustrato in questa sezione.
::: moniker-end

> [!Tip]
> Senza un progetto, tutte le versioni di Visual Studio funzionano correttamente con il codice Python. Ad esempio, è possibile aprire un file Python e usare le funzionalità IntelliSense, di completamento automatico e di debug facendo clic con il pulsante destro del mouse nell'editor e scegliendo **Avvia eseguendo debug**. Dal momento che tale codice usa sempre l'ambiente globale predefinito, è però possibile notare completamenti non corretti o completamenti errati se il codice è destinato a un ambiente diverso. Visual Studio inoltre analizza tutti i file e tutti i pacchetti presenti nella cartella da cui viene aperto il singolo file e questo potrebbe causare un notevole consumo del tempo della CPU.
>
> Creare un progetto di Visual Studio da codice esistente è davvero semplicissimo, come descritto in [Creare un progetto da file esistenti](#create-project-from-existing-files).

![Icona della fotocamera del film per il video](../install/media/video-icon.png "Guardare un video") Deep [Dive: Usare il controllo](https://youtu.be/Aq8eqApnugM) del codice sorgente con progetti Python (youtube.com, 8m 55s).

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Aggiungere file, assegnare un file di avvio e impostare gli ambienti

Durante lo sviluppo dell'applicazione è in genere necessario aggiungere al progetto nuovi file di tipi diversi. Per aggiungere tali file, fare clic con il pulsante destro del mouse sul progetto e scegliere Aggiungi elemento esistente con cui cercare un file da aggiungere oppure Aggiungi nuovo elemento , che visualizza una finestra di dialogo con diversi modelli di  >     >  elemento. Come descritto nel riferimento ai [modelli di elemento](python-item-templates.md), le opzioni includono file Python vuoti, una classe Python, uno unit test e diversi file correlati ad applicazioni Web. È possibile esaminare queste opzioni usando un progetto di test per scoprire quali elementi sono inclusi nella propria versione di Visual Studio.

A ogni progetto Python è assegnato un file di avvio, evidenziato in grassetto in **Esplora soluzioni**. Il file di avvio è il file che viene eseguito quando si avvia il debug (**F5** o Debug Avvia debug ) o quando si esegue il progetto nella finestra interattiva  >  (**MAIUSC**  + **ALT** + **F5**   >  o Debug Esegui progetto in Python Interactive ). Per modificare il valore, fare clic con il pulsante destro del mouse sul nuovo file e scegliere **Imposta come elemento di avvio** (o **Imposta come file di avvio** nelle versioni precedenti di Visual Studio).

> [!Tip]
> Se si rimuove il file di avvio selezionato da un progetto e non se ne seleziona uno nuovo, Visual Studio non sa quale file di Python usare per l'avvio quando si tenta di eseguire il progetto. In questo caso, Visual Studio 2017 versione 15.6 e versioni successive visualizzano un errore. Le versioni precedenti aprono una finestra di output con l'interprete Python in esecuzione oppure la finestra di output viene visualizzata ma scompare quasi immediatamente. In presenza di questi comportamenti, verificare che sia stato assegnato un file di avvio.
>
> Se si vuole mantenere aperta la finestra di output per qualsiasi motivo, fare clic con il pulsante destro del mouse sul progetto, scegliere **Proprietà**, selezionare la scheda **Debug** e quindi aggiungere `-i` al campo **Argomenti dell'interprete**. Questo argomento fa sì che l'interprete entri in modalità interattiva al termine di un programma, mantenendo la finestra aperta fino a quando non si immette **CTRL** + **Z**  >  **INVIO** per uscire.

::: moniker range="vs-2017"
Un nuovo progetto è sempre associato all'ambiente Python globale predefinito. Per associare il progetto a un altro ambiente (inclusi gli ambienti virtuali), fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** nel progetto, scegliere **Aggiungi/Rimuovi ambienti Python** e selezionare quelli desiderati.
::: moniker-end
::: moniker range=">=vs-2019"
Un nuovo progetto è sempre associato all'ambiente Python globale predefinito. Per associare il progetto a un altro ambiente (inclusi gli ambienti virtuali), fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** nel progetto, scegliere **Aggiungi ambiente** e selezionare quelli desiderati. È anche possibile usare l'elenco a discesa degli ambienti sulla barra degli strumenti per selezionare un ambiente o aggiungerne un altro per il progetto.

![Comando Aggiungi ambiente sulla barra degli strumenti Python](media/environments/environments-toolbar-2019.png)
::: moniker-end

Per cambiare l'ambiente attivo, fare clic con il pulsante destro del mouse sull'ambiente desiderato in **Esplora soluzioni** e scegliere **Attiva ambiente**, come illustrato di seguito. Per altre informazioni, vedere [Selezionare un ambiente per un progetto](selecting-a-python-environment-for-a-project.md).

![Attivazione di un ambiente per un progetto Python](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Modelli di progetto

In Visual Studio sono disponibili diverse opzioni per configurare un progetto Python, sia partendo da zero che da codice esistente. Per usare un modello, selezionare il comando di menu **File** Nuovo progetto o fare clic con il pulsante destro del mouse sulla soluzione in Esplora soluzioni e scegliere Aggiungi nuovo progetto , che verrà visualizzata la finestra di dialogo Nuovo progetto riportata di  >    >      >  seguito.  Per visualizzare i modelli specifici di Python, cercare "Python" o selezionare il **nodo**  >  **Python** installato:

![Finestra di dialogo Nuovo progetto con modelli Python](media/projects-new-project-dialog.png)

::: moniker range="<=vs-2017"

La tabella seguente riepiloga i modelli disponibili in Visual Studio 2017 (non tutti i modelli sono disponibili nelle versioni precedenti):

| Modello | Descrizione |
| --- | --- |
| [**Da codice Python esistente**](#create-project-from-existing-files) | Crea un progetto di Visual Studio da codice Python esistente in una struttura di cartelle.  |
| **Applicazione Python** | Struttura di progetto di base per una nuova applicazione Python che contiene un solo file di origine vuoto. Per impostazione predefinita, il progetto viene eseguito nell'interprete della console dell'ambiente globale predefinito, che è possibile modificare [assegnando un altro ambiente](selecting-a-python-environment-for-a-project.md). |
| [**Servizio cloud di Azure**](python-azure-cloud-service-project-template.md) | Progetto per un servizio cloud di Azure scritto in Python. |
| [**Progetti Web**](python-web-application-project-templates.md) | Progetti per le app Web basati su diversi framework, tra cui Bottle, Django e Flask. |
| **Applicazione IronPython** | È simile al modello Applicazione Python, ma usa IronPython per impostazione predefinita e abilita l'interoperabilità .NET e il debug in modalità mista con i linguaggi .NET. |
| **Applicazione WPF IronPython** | Struttura di progetto che usa IronPython con file XAML di Windows Presentation Foundation per l'interfaccia utente dell'applicazione. Visual Studio offre una finestra di progettazione dell'interfaccia utente XAML, il code-behind può essere scritto in Python e l'applicazione viene eseguita senza visualizzare alcuna console. |
| **Pagina Web IronPython Silverlight** | Progetto IronPython che viene eseguito in un browser con Silverlight. Il codice Python dell'applicazione è incluso nella pagina Web come script. Un tag di script boilerplate estrae parte del codice JavaScript che inizializza l'esecuzione di IronPython all'interno di Silverlight, da cui il codice Python può interagire con il DOM. |
| **Windows Forms Application IronPython** | Struttura di progetto che usa IronPython con l'interfaccia utente creata tramite il codice con Windows Forms. L'applicazione viene eseguita senza visualizzare alcuna console. |
| **Applicazione in background (IoT)** | Supporta la distribuzione di progetti Python per l'esecuzione nei dispositivi come servizi in background. Per altre informazioni, vedere la pagina di [Windows Dev Center dedicata a IoT](https://dev.windows.com/en-us/iot). |
| **Modulo di estensione Python** | Questo modello viene visualizzato in Visual C++ se sono stati installati gli **Strumenti di sviluppo nativi Python** con il carico di lavoro Python in Visual Studio 2017 o versioni successive (vedere [Installazione](installing-python-support-in-visual-studio.md)). Offre la struttura di base per una DLL di estensione C++, simile a quella descritta in [Create a C++ Extension for Python](working-with-c-cpp-python-in-visual-studio.md) (Creare un'estensione C++ per Python). |
::: moniker-end

::: moniker range=">=vs-2019"

La tabella seguente riepiloga i modelli disponibili in Visual Studio 2019 (non tutti i modelli sono disponibili in tutte le versioni precedenti):

| Modello | Descrizione |
| --- | --- |
| [**Da codice Python esistente**](#create-project-from-existing-files) | Crea un progetto di Visual Studio da codice Python esistente in una struttura di cartelle.  |
| **Applicazione Python** | Struttura di progetto di base per una nuova applicazione Python che contiene un solo file di origine vuoto. Per impostazione predefinita, il progetto viene eseguito nell'interprete della console dell'ambiente globale predefinito, che è possibile modificare [assegnando un altro ambiente](selecting-a-python-environment-for-a-project.md). |
| [**Progetti Web**](python-web-application-project-templates.md) | Progetti per le app Web basati su diversi framework, tra cui Bottle, Django e Flask. |
| **Applicazione IronPython** | È simile al modello Applicazione Python, ma usa IronPython per impostazione predefinita e abilita l'interoperabilità .NET e il debug in modalità mista con i linguaggi .NET. |
| **Applicazione WPF IronPython** | Struttura di progetto che usa IronPython con file XAML di Windows Presentation Foundation per l'interfaccia utente dell'applicazione. Visual Studio offre una finestra di progettazione dell'interfaccia utente XAML, il code-behind può essere scritto in Python e l'applicazione viene eseguita senza visualizzare alcuna console. |
| **Pagina Web IronPython Silverlight** | Progetto IronPython che viene eseguito in un browser con Silverlight. Il codice Python dell'applicazione è incluso nella pagina Web come script. Un tag di script boilerplate estrae parte del codice JavaScript che inizializza l'esecuzione di IronPython all'interno di Silverlight, da cui il codice Python può interagire con il DOM. |
| **Windows Forms Application IronPython** | Struttura di progetto che usa IronPython con l'interfaccia utente creata tramite il codice con Windows Forms. L'applicazione viene eseguita senza visualizzare alcuna console. |
| **Applicazione in background (IoT)** | Supporta la distribuzione di progetti Python per l'esecuzione nei dispositivi come servizi in background. Per altre informazioni, vedere la pagina di [Windows Dev Center dedicata a IoT](https://dev.windows.com/en-us/iot). |
| **Modulo di estensione Python** | Questo modello viene visualizzato in Visual C++ se sono stati installati gli **Strumenti di sviluppo nativi Python** con il carico di lavoro Python in Visual Studio 2017 o versioni successive (vedere [Installazione](installing-python-support-in-visual-studio.md)). Offre la struttura di base per una DLL di estensione C++, simile a quella descritta in [Create a C++ Extension for Python](working-with-c-cpp-python-in-visual-studio.md) (Creare un'estensione C++ per Python). |
::: moniker-end

> [!Note]
> Poiché Python è un linguaggio interpretato, i progetti Python in Visual Studio non producono un file eseguibile autonomo come altri progetti di linguaggi compilati (ad esempio, C#). Per altre informazioni, vedere le [domande e risposte](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Creare un progetto da file esistenti

> [!Important]
> Il processo descritto non sposta o copia i file di origine. Se si vuole usare una copia, per prima cosa duplicare la cartella.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>File collegati

Per file collegati si intendono i file importati in un progetto, ma che in genere si trovano all'esterno delle cartelle di progetto dell'applicazione. Tali file vengono visualizzati in **Esplora soluzioni** come file normali contraddistinti da un'icona di collegamento sovrapposta: ![icona file collegati](media/projects-linked-file-icon.png)

Questi file collegati vengono specificati nel file con estensione *pyproj* usando l'elemento `<Compile Include="...">`. I file collegati sono impliciti se usano un percorso relativo all'esterno della struttura di directory o espliciti se usano percorsi all'interno Esplora soluzioni **:**

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

In presenza delle condizioni seguenti i file collegati vengono ignorati:

- Il file collegato contiene metadati Link e il percorso specificato nell'attributo Include è presente all'interno della directory di progetto.
- Il file collegato duplica un file esistente nella gerarchia del progetto
- Il file collegato contiene metadati Link e il percorso di Link è un percorso relativo esterno alla gerarchia del progetto.
- Il percorso del collegamento è completo.

### <a name="work-with-linked-files"></a>Usare file collegati

Per aggiungere un elemento esistente come collegamento, fare clic con il pulsante destro del mouse sulla cartella nel progetto in cui si vuole aggiungere il file, quindi scegliere **Aggiungi**  >  **elemento esistente**. Nella finestra di dialogo visualizzata, selezionare un file e scegliere **Aggiungi come collegamento** nell'elenco a discesa del pulsante **Aggiungi**. Questo comando crea un collegamento nella cartella selezionata, purché non siano presenti file in conflitto. Il collegamento non verrà aggiunto se però è già presente un file con lo stesso nome o nel progetto esiste già un collegamento a tale file.

Se si prova a collegare un file già esistente nelle cartelle di progetto, questo viene aggiunto come un file normale e non come collegamento. Per convertire un file in un collegamento, selezionare **Salva** con nome per salvare il file in un percorso esterno  >   alla gerarchia del progetto. Visual Studio lo converte automaticamente in un collegamento. Analogamente, un collegamento può essere convertito nuovamente usando Salva con nome **per** salvare il file in un punto qualsiasi  >   all'interno della gerarchia del progetto.

Se si sposta un file collegato in **Esplora soluzioni**, viene spostato solo il collegamento, mentre il file effettivo rimane nella posizione originale. Analogamente, l'eliminazione di un collegamento implica solo la rimozione del collegamento e non del file.

I file collegati non possono essere rinominati.

## <a name="references"></a>Riferimenti

Nei progetti Visual Studio è possibile aggiungere riferimenti a progetti ed estensioni che figureranno nel nodo **Riferimenti** in **Esplora soluzioni**:

![Riferimenti alle estensioni in progetti Python](media/projects-extension-references.png)

I riferimenti alle estensioni indicano in genere le dipendenze tra progetti e vengono usati per fornire funzionalità IntelliSense in fase di progettazione o di collegamento in fase di compilazione. I riferimenti vengono usati in modo analogo nei progetti Python, ma a causa della natura dinamica di Python vengono usati principalmente in fase di progettazione per fornire funzionalità IntelliSense migliorate. Possono inoltre essere usati per la distribuzione in Microsoft Azure per installare le dipendenze aggiuntive.

### <a name="extension-modules"></a>Moduli di estensione

Un riferimento a un file con estensione *pyd* consente di abilitare la funzionalità IntelliSense per il modulo generato. Visual Studio carica il file con estensione *pyd* nell'interprete Python e ne esamina tipi e funzioni. Prova inoltre ad analizzare le stringhe di documento relative alle funzioni per offrire il supporto per la firma.

Se in qualsiasi momento il modulo di estensione viene aggiornato sul disco, Visual Studio analizza nuovamente il modulo in background. Questa azione non ha effetto sul comportamento in fase di esecuzione, ma alcuni completamenti non sono disponibili fino al completamento dell'analisi.

Potrebbe anche essere necessario aggiungere un [percorso di ricerca](search-paths.md) per la cartella che contiene il modulo.

### <a name="net-projects"></a>Progetti .NET

Quando si usa IronPython, è possibile aggiungere riferimenti ad assembly .NET per abilitare la funzionalità IntelliSense. Per i progetti .NET presenti nella soluzione fare clic con il pulsante destro del mouse sul nodo **Riferimenti** del progetto Python, scegliere **Aggiungi riferimento**, selezionare la scheda **Progetti** e quindi individuare e selezionare il progetto desiderato. Per le DLL scaricate separatamente, selezionare la scheda **Sfoglia** e quindi individuare e selezionare la DLL desiderata.

Dato che i riferimenti in IronPython non sono disponibili fino a quando non si effettua una chiamata a `clr.AddReference('<AssemblyName>')`, è anche necessario aggiungere una chiamata `clr.AddReference` appropriata all'assembly, in genere all'inizio del codice. Ad esempio, il codice creato dal modello di progetto dell'**applicazione Windows Forms IronPython** in Visual Studio include due chiamate nella parte superiore del file:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>Progetti WebPI

È possibile aggiungere riferimenti alle voci di prodotto WebPI per la distribuzione nei servizi cloud di Microsoft Azure in cui è possibile installare componenti aggiuntivi tramite il feed WebPI. Per impostazione predefinita, il feed visualizzato è specifico di Python e include Django, CPython e altri componenti di base. È inoltre possibile selezionare un feed personalizzato, come illustrato di seguito. Durante la pubblicazione in Microsoft Azure, un'attività di installazione installerà tutti i prodotti di riferimento.

> [!IMPORTANT]
> I progetti WebPI non sono disponibili in Visual Studio 2017 o Visual Studio 2019.

![Riferimenti WebPI](media/projects-webPI-components.png)
