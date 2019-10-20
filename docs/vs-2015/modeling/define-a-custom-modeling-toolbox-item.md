---
title: Definire un elemento personalizzato della casella degli strumenti di modellazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 27692c31c2c0f1c52ab026fb2d55e5d240839ff3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654894"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Definire un elemento della casella degli strumenti di modellazione personalizzata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per semplificare la creazione di un elemento o di un gruppo di elementi in base a un modello usato di frequente, è possibile aggiungere nuovi strumenti alla casella degli strumenti dei diagrammi di modellazione in Visual Studio. È possibile distribuire questi elementi della casella degli strumenti ad altri utenti di Visual Studio.

 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Uno strumento personalizzato crea uno o più nuovi elementi in un diagramma. Ad esempio, è possibile creare uno strumento personalizzato per creare gli elementi seguenti:

- Un pacchetto collegato al profilo .NET e una classe con lo stereotipo .NET.

- Una coppia di classi collegate da un'associazione per rappresentare il modello Observer.

> [!NOTE]
> È possibile usare questo metodo per creare strumenti elemento. È quindi possibile creare strumenti che è possibile trascinare dalla casella degli strumenti in un diagramma. Non è possibile creare strumenti connettore.

## <a name="DefineTool"></a>Definizione di uno strumento di modellazione personalizzato

#### <a name="to-define-a-custom-modeling-tool"></a>Per definire un strumento di modellazione personalizzato

1. Creare un diagramma UML che contiene un elemento o un gruppo di elementi.

    - Questi elementi possono presentare relazioni tra loro e possono contenere elementi sussidiari quali porte, attributi, operazioni o PIN.

2. Salvare il diagramma usando il nome che si desidera assegnare al nuovo strumento. Scegliere Salva dal menu **file** **... Come**.

3. Usando Esplora risorse, copiare i due file diagramma nella cartella seguente o in qualsiasi sottocartella:

     *YourDocuments* **\Visual Studio\Architecture Tools\Custom elementi della casella degli strumenti**

    - Creare questa cartella se non esiste già. Potrebbe essere necessario creare entrambi gli **strumenti di architettura** e **gli elementi personalizzati della casella degli strumenti**.

    - Copiare entrambi i file di diagramma, uno con un nome che termina con "... **diagramma**"e l'altro con un nome che termina con"... **diagramma. layout**"

    - È possibile creare tanti strumenti personalizzati nel modo desiderato. Usare un diagramma per ogni strumento.

4. Opzionale Creare un file con **estensione tbxinfo** come descritto in [come definire le proprietà degli strumenti personalizzati](#tbxinfo)e aggiungerlo alla stessa directory. Consente di definire un'icona casella degli strumenti, un suggerimento e così via.

    - Per definire diversi strumenti, è possibile usare un singolo file con **estensione tbxinfo** . Può fare riferimento ai file diagramma presenti nelle sottocartelle.

5. Riavviare Visual Studio. Lo strumento aggiuntivo verrà visualizzato nella casella degli strumenti per il tipo di diagramma appropriato.

### <a name="what-the-custom-tool-will-replicate"></a>Cosa verrà replicato dallo strumento personalizzato
 Uno strumento personalizzato replicherà la maggior parte delle funzionalità del diagramma di origine:

- Nomi. Quando viene creato un elemento dalla casella degli strumenti, viene aggiunto un numero alla fine del nome, se necessario, per evitare nomi duplicati nello stesso spazio dei nomi.

- Colori, dimensioni e forme

- Profili di pacchetti e stereotipi

- Valori delle proprietà come Abstract

- Elementi di lavoro collegati

- Molteplicità e altre proprietà delle relazioni

- Le posizioni relative delle forme.

  Le funzionalità seguenti non verranno mantenute in uno strumento personalizzato:

- Forme semplici. Si tratta di forme che non sono correlate a elementi modello, che è possibile creare in alcuni tipi di diagrammi.

- Connettore di routing. Se si instradano connettori manualmente, il routing non verrà mantenuto quando si usa lo strumento. Le posizioni di alcune forme annidate, come le porte, non vengono mantenute relativamente ai proprietari.

## <a name="tbxinfo"></a>Come definire le proprietà degli strumenti personalizzati
 Un file di informazioni della casella degli strumenti (con**estensione tbxinfo**) consente di specificare un nome della casella degli strumenti, un'icona, una descrizione comando, una scheda e una parola chiave della Guida per uno o più strumenti personalizzati. Assegnargli un nome, ad esempio **tbxinfo**.

 Il formato generale del file è il seguente:

```
<?xml version="1.0" encoding="utf-8" ?>
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">
  <customToolboxItem fileName="MyObserverTool.classdiagram">
    <displayName>
       <value>Observer Pattern</value>
    </displayName>
    <tabName>
       <value>UML Class Diagram</value>
    </tabName>
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>
    <f1Keyword>
      <value>ObserverPatternHelp</value>
    </f1Keyword>
    <tooltip>
       <value>Create a pair of classes</value>
    </tooltip>
  </customToolboxItem>
</customToolboxItems>
```

 Il valore di ogni elemento può essere:

- Come illustrato nell'esempio, `<bmp fileName="…"/>` per l'icona della casella degli strumenti e `<value>string</value>` per gli altri elementi.

  \- oppure -

- `<resource fileName="Resources.dll"`

   `baseName="Observer.resources" id="Observer.tabname" />`

   In questo caso, è necessario fornire un assembly compilato in cui sono stati compilati i valori stringa come risorse.

  Aggiungere un nodo `<customToolboxItem>` per ogni elemento della casella degli strumenti che si intende definire.

  I nodi nel file con **estensione tbxinfo** sono i seguenti. Esiste un valore predefinito per ogni nodo.

|Nome nodo|Definisce|
|---------------|-------------|
|displayName|Il nome dell'elemento della casella degli strumenti.|
|tabName|La scheda casella degli strumenti in cui l'elemento verrà visualizzato. È possibile specificare il nome della scheda standard per questo tipo di diagramma o un nome distinto.|
|immagine|Il percorso del file bitmap ( **. bmp**), che deve avere altezza e larghezza pari a 16 e una profondità di colore di 24 bit.|
|f1Keyword|La parola chiave che individua un argomento della Guida.|
|descrizione comando|Una descrizione comandi per questo strumento.|

 È possibile modificare il file bitmap in Visual Studio e impostare l'altezza e larghezza su 16 nella finestra Proprietà.

> [!NOTE]
> Se si inizia a usare un file con estensione tbxinfo dopo qualche esperimento con l'utilizzo dei file diagramma in modo autonomo, si noterà che la casella degli strumenti contiene le versioni vecchie e nuove di un elemento della casella degli strumenti. È possibile che ciò si verifichi anche se il nome del file diagramma è stato digitato in modo errato nel file con estensione tbxinfo. In tal caso, scegliere **Reimposta casella**degli strumenti dal menu di scelta rapida della casella degli strumenti. Gli elementi della casella degli strumenti personalizzata verranno rimossi. Riavviare Visual Studio e verranno visualizzati gli elementi personalizzati corretti.

## <a name="Extension"></a>Come distribuire elementi della casella degli strumenti in un'estensione di Visual Studio
 È possibile distribuire gli elementi della casella degli strumenti ad altri [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utenti creandone un pacchetto in un'estensione di Visual Studio (VSIX). È possibile comprimere comandi, profili e altre estensioni nello stesso file VSIX. Per ulteriori informazioni, vedere [distribuzione delle estensioni di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160780).

 Il modo consueto per compilare un'estensione di Visual Studio consiste nell'usare il modello di progetto VSIX. A tale scopo, è necessario avere installato [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>Per aggiungere un elemento della casella degli strumenti a un'estensione di Visual Studio

1. [Creare e testare uno o più strumenti personalizzati](#DefineTool).

2. [Creare un file con estensione tbxinfo](#tbxinfo) che faccia riferimento agli strumenti.

3. Aprire un progetto di estensione di Visual Studio esistente.

     \- oppure -

     Aprire un nuovo progetto di estensione di Visual Studio.

    1. Nel menu **File** , scegliere **Nuovo**, **Progetto**.

    2. Nella finestra di dialogo **nuovo progetto** , in **modelli installati**, scegliere **Visual C#** , **Extensibility**, **progetto VSIX**.

4. Aggiungere le definizioni della casella degli strumenti al progetto. Includere il file con **estensione tbxinfo** , i file di diagramma, i file bitmap e tutti i file di risorse e assicurarsi che siano inclusi in VSIX.

    - In Esplora soluzioni scegliere **Aggiungi**, **elemento esistente**dal menu di scelta rapida del progetto VSIX. Nella finestra di dialogo impostare **oggetti di tipo: tutti i file**. Individuare i file, selezionarli tutti, quindi scegliere **Aggiungi**.

        > [!NOTE]
        > In questo progetto non è possibile aprire i file del diagramma nell'editor del modello.

5. Impostare le seguenti proprietà di tutti i file appena aggiunti. È possibile impostare le relative proprietà contemporaneamente selezionandole tutte in Esplora soluzioni. Prestare attenzione a non modificare le proprietà degli altri file nel progetto.

     **Copia nella directory di Output**  = **copia sempre**

     **Azione di compilazione**  = **contenuto**

     **Includi in VSIX**  = **true**

6. Aprire **source.extension.vsixmanifest**. Viene aperto nell'editor del manifesto dell'estensione.

7. In **metadati**aggiungere una descrizione per gli strumenti personalizzati.

     In **Asset**scegliere **nuovo** e quindi impostare i campi nella finestra di dialogo come segue:

    - **Digitare**  = **tipo di estensione personalizzato**

    - Tipo = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`

        > [!NOTE]
        > Questa opzione non è inclusa nell'elenco a discesa. È necessario immetterla mediante tastiera.

    - **File di  =  di origine nel file System**.

    - **Path** = il file con **estensione tbxinfo** , ad esempio, **strumenti. tbxinfo**

8. Compilare il progetto.

9. **Per verificare il funzionamento dell'estensione**, premere F5. Viene avviata l'istanza sperimentale di Visual Studio.

     Nell'istanza sperimentale creare o aprire un diagramma UML del tipo pertinente. Verificare che venga visualizzato il nuovo strumento nella casella degli strumenti e che vengano creati correttamente gli elementi.

10. **Per ottenere un file VSIX per la distribuzione:** In Esplora risorse aprire la cartella **.\bin\Debug** o **.\bin\Release** per trovare il file con estensione **VSIX** . Si tratta di un file di estensione [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Può essere installato nel computer e inviato anche ad altri utenti di Visual Studio.

#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Per installare gli strumenti personalizzati da un'estensione di Visual Studio

1. Aprire il file `.vsix` in Esplora risorse o in Visual Studio.

2. Scegliere **Installa** nella finestra di dialogo visualizzata.

3. Per disinstallare o disabilitare temporaneamente l'estensione, aprire **estensioni e aggiornamenti** dal menu **strumenti** .

## <a name="localization"></a>Localizzazione
 È possibile creare un'estensione che, quando viene installata su un altro computer, verranno visualizzati i nomi dello strumento e le descrizioni comandi nella lingua del computer di destinazione.

#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>Per fornire versioni dello strumento in più lingue

1. Creare un progetto Visual Studio Extension che contiene uno o più strumenti personalizzati.

    Nel file con **estensione tbxinfo** usare il metodo del file di risorse per definire la `displayName` dello strumento, la casella degli strumenti `tabName` e la descrizione comando. Creare un file di risorse in cui queste stringhe sono definite, compilarlo in un assembly e farvi riferimento dal file con estensione tbxinfo.

2. Creare assembly aggiuntivi che contengono file di risorse con stringhe di altre lingue.

3. Posizionare ogni assembly aggiuntivo in una cartella il cui nome sia il codice delle impostazioni cultura per la lingua. Inserire, ad esempio, una versione francese dell'assembly all'interno di una cartella denominata **fr**.

4. È consigliabile usare un codice indipendente dalle impostazioni cultura, in genere costituito da due lettere, non il codice delle impostazioni cultura specifiche come ad esempio `fr-CA`. Per ulteriori informazioni sui codici delle impostazioni cultura, vedere [Metodo CultureInfo. GetCultures](http://go.microsoft.com/fwlink/?LinkId=160782), che fornisce un elenco completo di codici delle impostazioni cultura.

5. Compilare progetto Visual Studio Extension e distribuirlo.

6. Quando l'estensione viene installata in un altro computer, verrà automaticamente caricata la versione del file di risorse per le impostazioni cultura locali dell'utente. Se non è stata fornita una versione per le impostazioni cultura dell'utente, verranno usate le risorse predefinite.

   Non è possibile usare questo metodo per installare versioni diverse del diagramma prototipo. I nomi degli elementi e dei connettori saranno gli stessi in ogni installazione.

## <a name="other-toolbox-operations"></a>Altre operazioni della casella degli strumenti
 Normalmente, in [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], è possibile personalizzare la casella degli strumenti rinominando gli strumenti, spostandoli in altre schede della casella degli strumenti ed eliminandoli. Queste modifiche non vengono mantenute per gli strumenti di modellazione personalizzati creati con le procedure descritte in questo argomento. Quando si riavvia [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], gli strumenti personalizzati verranno visualizzati nuovamente con i nomi e i percorsi definiti della casella degli strumenti.

 Inoltre, gli strumenti personalizzati scompariranno se si esegue il comando **Reimposta casella degli strumenti** . Verranno però visualizzati nuovamente quando si riavvia [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

## <a name="see-also"></a>Vedere anche
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md) [definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md) [definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md)
