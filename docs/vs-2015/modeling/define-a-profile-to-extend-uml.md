---
title: Definire un profilo per estendere UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b256971cd327098e22b243a1c171b0c9e82d32bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433137"
---
# <a name="define-a-profile-to-extend-uml"></a>Definire un profilo per estendere UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile definire un *profilo UML* per personalizzare gli elementi del modello standard per scopi specifici. Un profilo definisce uno o più *stereotipi UML*. Uno stereotipo può essere utilizzato per contrassegnare un tipo come rappresentazione di un determinato tipo di oggetto. Uno stereotipo può anche essere usato per estendere l'elenco di proprietà di un elemento.  
  
 Vengono installati diversi profili con le edizioni supportate di Visual Studio. Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). Per altre informazioni su questi profili e su come applicare gli stereotipi, vedere [personalizzare il modello con profili e stereotipi](../modeling/customize-your-model-with-profiles-and-stereotypes.md).  
  
 È possibile definire i propri profili per adattare ed estendere il linguaggio UML alla propria architettura o area aziendale. Ad esempio:  
  
- Se si definiscono spesso siti Web, si può definire un proprio profilo che fornisca uno stereotipo «WebPage» applicabile alle classi nei diagrammi classi. Sarebbe quindi possibile usare i diagrammi classi per pianificare un sito Web. Ogni classe «WebPage» avrebbe proprietà aggiuntive per il contenuto della pagina, lo stile e così via.  
  
- Se si sviluppa software di e-banking, si potrebbe definire un profilo che fornisca uno stereotipo «Account». Sarebbe quindi possibile usare i diagrammi classi per definire tipi diversi di conto e mostrare le relazioni tra di essi.  
  
  È possibile distribuire i propri profili al team. Ogni membro del team può installare il profilo. Ciò consente di modificare e creare modelli che usano i relativi stereotipi.  
  
> [!NOTE]
> Se si applicano gli stereotipi di un profilo in un modello che si sta modificando e quindi si condivide il modello con altre persone, queste devono installare lo stesso profilo nei propri computer. In caso contrario, non saranno in grado di visualizzare gli stereotipi usati.  
  
 Un profilo fa spesso parte di una maggiore [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] estensione. Ad esempio, si può definire un comando che traduce alcune parti di un modello in codice. È possibile definire un profilo che gli utenti devono applicare ai pacchetti che vogliono tradurre. È possibile distribuire il nuovo comando insieme al profilo in una singola estensione di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
 È inoltre possibile definire varianti localizzate di un profilo. Gli utenti che caricano l'estensione visualizzano la variante appropriata alle proprie impostazioni cultura.  
  
## <a name="DefineProfile"></a> Come definire un profilo  
  
#### <a name="to-define-a-uml-profile"></a>Per definire un profilo UML  
  
1. Creare un nuovo file XML con l'estensione di file `.profile`.  
  
2. Aggiungere definizioni di stereotipo secondo le linee guida descritte nel [struttura di un profilo](#Schema).  
  
3. Aggiungere il profilo a un'estensione di Visual Studio (file `.vsix`). È possibile creare una nuova estensione per il profilo o aggiungere il profilo a un'estensione esistente.  
  
     Vedere la sezione successiva [come aggiungere un profilo a un'estensione di Visual Studio](#AddProfile).  
  
4. Installare l'estensione nel computer.  
  
    1. Fare doppio clic sul file dell'estensione, che ha un'estensione di file `.vsix`.  
  
    2. Riavviare Visual Studio.  
  
5. Verificare che il profilo sia stato installato.  
  
    1. Selezionare il modello in Esplora UML.  
  
    2. Nella finestra Proprietà scegliere il **profili** proprietà. Il profilo verrà visualizzato nel menu. Impostare il segno di spunta accanto al profilo.  
  
    3. Selezionare un elemento per cui il profilo definisce gli stereotipi. Nella finestra Proprietà scegliere il **stereotipi** proprietà. Gli stereotipi verranno visualizzati nell'elenco. Impostare il segno di spunta accanto a uno degli stereotipi.  
  
    4. Se il profilo definisce altre proprietà per questo stereotipo, espandere la proprietà dello stereotipo per visualizzarle.  
  
6. Inviare il file dell'estensione ad altri utenti di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] che lo installeranno nei rispettivi computer.  
  
## <a name="AddProfile"></a> Come aggiungere un profilo a un'estensione di Visual Studio  
 Per installare un profilo e poterlo inviare ad altri utenti, è necessario aggiungerlo a un'estensione di Visual Studio. Per altre informazioni, vedere [distribuzione di estensioni di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160780).  
  
#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>Per definire un profilo in una nuova estensione di Visual Studio  
  
1. Creare un progetto di estensione di Visual Studio  
  
   > [!NOTE]
   > È necessario avere installato [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] per usare questa procedura.  
  
   1. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
   2. Nel **nuovo progetto** nella finestra di dialogo **modelli installati**, espandere **Visual c#**, fare clic su **estendibilità**, quindi fare clic su  **Progetto VSIX**. Impostare il nome del progetto e scegliere **OK**.  
  
2. Aggiungere il profilo al progetto.  
  
   - In Esplora soluzioni fare clic sul progetto, scegliere **Add**, quindi fare clic su **elemento esistente**. Nella finestra di dialogo individuare il file del profilo.  
  
3. Impostare il file di profilo **Copia output** proprietà.  
  
   1. In Esplora soluzioni fare doppio clic su file del profilo e quindi fare clic su **proprietà**.  
  
   2. Nella finestra Proprietà impostare il **copia in Directory di Output** proprietà **Copia sempre**.  
  
4. In Esplora soluzioni aprire `source.extension.vsixmanifest`.  
  
    Il file viene aperto nell'editor del manifesto dell'estensione.  
  
5. Nel **asset** pagina, aggiungere una riga che descrive il profilo:  
  
   - Fare clic su **Nuovo**. Impostare i campi nella **Aggiungi nuovo Asset** finestra di dialogo come indicato di seguito.  
  
   - Impostare **tipo** a `Microsoft.VisualStudio.UmlProfile`  
  
        Non si tratta di una delle opzioni a discesa. Inserire il nome utilizzando la tastiera.  
  
   - Fare clic su **File in filesystem** e selezionare il nome del file di profilo, ad esempio `MyProfile.profile`  
  
6. Compilare il progetto.  
  
7. **Per eseguire il debug del profilo**, premere F5.  
  
    Viene aperta un'istanza sperimentale di Visual Studio. In questa istanza aprire un progetto di modellazione. In Esplora modelli UML selezionare l'elemento radice del modello, quindi nella finestra Proprietà selezionare il profilo. Selezionare gli elementi nel modello e impostare gli stereotipi che sono stati definiti per essi.  
  
8. **Per estrarre il file VSIX per la distribuzione**  
  
   1. In Windows Explorer, aprire la cartella **.\bin\Debug** oppure **.\bin\Release** per trovare i **VSIX** file. Si tratta di un file di estensione [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Può essere installato nel computer e inviato ad altri utenti di Visual Studio.  
  
   2. Per installare l'estensione:  
  
       1. Fare doppio clic sul file `.vsix`. Verrà avviato Visual Studio Extension Installer.  
  
       2. Riavviare tutte le istanze di Visual Studio in esecuzione.  
  
   La seguente procedura alternativa può essere usata per estensioni di piccole dimensioni se [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] non è stato installato.  
  
#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>Per definire un'estensione del profilo senza usare Visual Studio SDK  
  
1. Creare una directory di Windows che contiene i tre file seguenti:  
  
    - *YourProfile* `.profile`  
  
    - `extension.vsixmanifest`  
  
    - `[Content_Types].xml`: digitare questo nome come mostrato qui, con le parentesi quadre  
  
2. Modificare `[Content_Types].xml` in modo che contenga il testo seguente. Si noti che contiene una voce per ogni estensione di file.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
      <Default Extension="profile" ContentType="application/octet-stream" />  
      <Default Extension="vsixmanifest" ContentType="text/xml" />  
    </Types>  
    ```  
  
3. Copiare un file `extension.vsixmanifest` esistente e modificarlo con un editor XML. Modificare i nodi ID, Name e Content.  
  
    - È possibile trovare un esempio di `extension.vsixmanifest` in questa directory:  
  
         *unità* **: \Programmi\Microsoft Visual Studio [versione] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles**  
  
    - Il nodo Content deve essere simile al seguente:  
  
        ```  
        <Content>  
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"  
          >YourProfile.Profile</CustomExtension>  
        </Content>  
        ```  
  
4. Comprimere i tre file in un file compresso.  
  
     In Windows Explorer, selezionare i tre file, fare doppio clic su, scegliere **Invia a**, quindi fare clic su **cartella compressa Compressed**.  
  
5. Rinominare il file compresso e cambiare l'estensione di file da `.zip` a `.vsix`.  
  
6. Per installare il profilo in qualsiasi computer con le edizioni appropriate di Visual Studio, fare doppio clic sul file `.vsix`.  
  
#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>Per installare un profilo UML da un'estensione di Visual Studio  
  
1. Fare doppio clic sul file `.vsix` in Esplora risorse o aprirlo in Visual Studio.  
  
2. Fare clic su **installare** nella finestra di dialogo visualizzata.  
  
3. Per disinstallare o disabilitare temporaneamente l'estensione, aprire **estensioni e aggiornamenti** dalle **Tools** menu.  
  
## <a name="Localized"></a> Come definire profili localizzati  
 È possibile definire profili diversi per impostazioni cultura o lingue diverse e comprimerli tutti nella stessa estensione. Quando un utente carica l'estensione, vedrà il profilo definito per le proprie impostazioni cultura.  
  
 È sempre necessario specificare un profilo predefinito. Se non è stato definito un profilo per le impostazioni cultura dell'utente, verrà visualizzato il profilo predefinito.  
  
#### <a name="to-define-a-localized-profile"></a>Per definire un profilo localizzato  
  
1. Creare un profilo, come descritto nelle sezioni precedenti[come definire un profilo](#DefineProfile) e [come aggiungere un profilo a un'estensione di Visual Studio](#AddProfile). Questo è il profilo predefinito e verrà usato in tutte le installazioni per cui non si specifica un profilo localizzato.  
  
2. Aggiungere una nuova directory nella stessa directory del file del profilo predefinito.  
  
    > [!NOTE]
    > Se si sta compilando l'estensione usando un progetto di estensione di Visual Studio, usare Esplora soluzioni per aggiungere una nuova cartella al progetto.  
  
3. Sostituire il nome della nuova directory con il codice breve ISO delle impostazioni cultura localizzate, ad esempio `bg` per il bulgaro o `fr` per il francese. È consigliabile usare un codice indipendente dalle impostazioni cultura, in genere costituito da due lettere, non il codice delle impostazioni cultura specifiche come ad esempio `fr-CA`. Per altre informazioni sui codici delle impostazioni cultura, vedere [metodo CultureInfo. GetCultures](http://go.microsoft.com/fwlink/?LinkId=160782), che fornisce un elenco completo dei codici delle impostazioni cultura.  
  
4. Aggiungere una copia del profilo predefinito alla nuova directory. Non modificare il nome file.  
  
     Un campione [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] cartella di estensione, prima che venga compilata o compressa in un `.vsix` file, può contenere le cartelle e file seguente:  
  
     `extension.vsixmanifest`  
  
     `MyProfile.profile`  
  
     `fr\MyProfile.profile`  
  
     `de\MyProfile.profile`  
  
    > [!NOTE]
    > Non è necessario inserire in `extension.vsixmanifest` un riferimento alle versioni localizzate dei profili. I file dei profili copiati devono avere lo stesso nome del profilo nella cartella padre.  
  
5. Modificare la nuova copia del profilo, traducendo nella lingua di destinazione tutte le parti che saranno visibili all'utente, ad esempio gli attributi `displayName`.  
  
6. È possibile creare altre cartelle di impostazioni cultura e profili localizzati per tutte le impostazioni cultura desiderate.  
  
7. Compilare l'estensione di Visual Studio, compilando il progetto di estensione o comprimendo tutti i file, come spiegato nelle precedenti sezioni.  
  
## <a name="Schema"></a> La struttura di un profilo  
 Il file XSD per i profili UML è reperibile nell'esempio seguente: [Impostazione di stereotipi e profili XSD](http://go.microsoft.com/fwlink/?LinkID=213811). Per facilitare la modifica dei file di profilo, installare il file `.xsd` in:  
  
 **%ProgramFiles%\Microsoft visual Studio [versione] \Xml\Schemas.**  
  
 Questa sezione usa il profilo C# come esempio. La definizione completa del profilo può essere visualizzata in:  
  
 *unità* **: \Programmi\Microsoft Visual Studio [versione] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\CSharp.profile**  
  
 Le prime parti di questo percorso potrebbero essere diverse nell'installazione in uso.  
  
 Per altre informazioni sul profilo .NET, vedere [stereotipi Standard per modelli UML](../modeling/standard-stereotypes-for-uml-models.md).  
  
### <a name="main-sections-of-the-uml-profile-definition"></a>Sezioni principali della definizione del profilo UML  
 Ogni profilo contiene quanto segue:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<profile dslVersion="1.0.0.0"   
       name="CSharpProfile" displayName="C# Profile"   
       xmlns="http://schemas.microsoft.com/UML2.1.2/ProfileDefinition">  
  <stereotypes>...</stereotypes>  
  <metaclasses>...</metaclasses>  
  <propertyTypes>...</propertyTypes>  
</profile>  
```  
  
> [!NOTE]
> L'attributo `name` non deve contenere spazi o punteggiatura. L'attributo `displayName`, visualizzato nell'interfaccia utente, deve essere una stringa XML valida.  
  
 Ogni profilo contiene tre sezioni principali. In ordine inverso, sono le seguenti:  
  
- `<propertyTypes>`: elenco di tipi usati per le proprietà definite nella sezione degli stereotipi.  
  
- `<metaclasses>`: elenco di tipi di elemento del modello a cui si applicano gli stereotipi di questo profilo, ad esempio IClass, IInterface, IOperation, IDependency.  
  
- `<stereotypes>`: definizioni degli stereotipi. Ogni definizione include i nomi e i tipi delle proprietà aggiunte all'elemento del modello di destinazione.  
  
#### <a name="property-types"></a>Tipi di proprietà  
 Il `<propertyTypes>` sezione dichiara un elenco di tipi usati per le proprietà di `<stereotypes>` sezione. Esistono due tipi di proprietà: esterno ed enumerazione.  
  
 Un tipo esterno dichiara il nome completo di un tipo .NET standard:  
  
```  
<externalType name="System.String" />  
```  
  
 Un tipo di enumerazione definisce un set di valori letterali:  
  
```  
<enumerationType name="PackageVisibility">  
  <enumerationLiterals>  
    <enumerationLiteral name="internal" displayName="internal"  />  
    <enumerationLiteral name="protectedinternal" displayName="protected internal" />  
  </enumerationLiterals>  
</enumerationType>  
```  
  
#### <a name="metaclasses"></a>Metaclassi  
 La sezione `<metaclasses>` è un elenco di tipi di elemento del modello per cui è possibile definire gli stereotipi in questo profilo:  
  
```  
<metaclass   
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />  
<metaclass  
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />  
<metaclass  
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />  
```  
  
 Per l'elenco completo dei tipi di relazioni e di elementi di modello che è possibile usare come metaclassi, vedere [tipi di elemento di modello](#Elements).  
  
#### <a name="stereotype-definition"></a>Definizione degli stereotipi  
 La sezione `<stereotypes>` contiene una o più definizioni di stereotipi:  
  
```  
<stereotype name="CSharpClass" displayName="C# Class"> ...  
```  
  
 Ogni stereotipo elenca uno o più tipi di relazioni o di elementi del modello a cui può essere applicato. È possibile assegnare il nome di un tipo di base, in modo da includere tutti i tipi derivati. Ad esempio, se si specifica `Microsoft.VisualStudio.Uml.Classes.IType`, lo stereotipo può essere applicato a `IClass`, `IInterface`, `IEnumeration` e a diversi altri tipi di elemento.  
  
```  
<metaclasses>  
  <metaclassMoniker name=  
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />  
</metaclasses>  
```  
  
 L'attributo `name` di `metaclassMoniker` è un collegamento a un elemento della sezione `<metaClasses>`.  
  
> [!NOTE]
> Il nome del moniker deve iniziare con `/yourProfileName/`, dove `yourProfileName` è definito nell'attributo `name` del profilo (in questo esempio, "CSharpProfile"). Il moniker termina con il nome di una delle voci nella sezione delle metaclassi.  
  
 Ogni stereotipo può elencare zero o più proprietà che aggiunge a tutti gli elementi del modello a cui viene applicato. Il `<propertyType>` contiene un collegamento a uno dei tipi definiti nel `<propertyTypes>` sezione. Il collegamento deve essere un oggetto `<externalTypeMoniker>` per fare riferimento a `<externalType>,` o un oggetto `<enumerationTypeMoniker>` per fare riferimento a `<enumerationType>`. Anche in questo caso, il collegamento inizia con il nome del profilo.  
  
```  
  <properties>  
    <property name="IsStatic"   
            displayName="Is Static" defaultValue="false">  
      <propertyType>  
<externalTypeMoniker   
               name="/CSharpProfile/System.Boolean" />  
      </propertyType>  
    </property>  
    <property name="PackageVisibility"   
              displayName="Package Visibility"  
              defaultValue="internal">  
      <propertyType>  
        <enumerationTypeMoniker   
              name="/CSharpProfile/PackageVisibility"/>  
      </propertyType>  
    </property>  
  </properties>  
</stereotype>  
```  
  
## <a name="Elements"></a> Tipi di elemento di modello  
 Il set di tipi per cui è possibile definire gli stereotipi è elencato [tipi di elemento di modello UML](../modeling/uml-model-element-types.md).  
  
## <a name="troubleshooting"></a>Risoluzione dei problemi  
 Gli stereotipi non vengono visualizzati nei modelli UML.  
 È necessario selezionare il profilo in un pacchetto o in un modello. Gli stereotipi verranno visualizzati negli elementi all'interno del pacchetto o del modello. Per altre informazioni, vedere [Add stereotipi UML di elementi del modello](../modeling/add-stereotypes-to-uml-model-elements.md).  
  
 Quando si apre un modello UML, viene visualizzato l'errore seguente: **VS1707: Poiché si è verificato un errore di serializzazione, non è possibile caricare i profili seguenti: MyProfile.profile**  
1. Verificare che la sintassi XML di base del file con estensione profile sia corretta.  
  
2. Assicurarsi che ogni nome di moniker sia nel formato /profileName/nodeName. profileName è il valore dell'attributo name nel nodo del profilo radice. nodeName è il valore dell'attributo name di una metaclasse, externalType o enumerationType.  
  
3. Verificare la sintassi sia come descritto qui, come illustrato nel _unità_**: \Programmi\Microsoft Visual Studio [versione] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\\** .  
  
4. Disinstallare l'estensione errata. Nel menu **Strumenti** fare clic su **Estensioni e aggiornamenti**.  
  
   - Se l'estensione non è visibile, vedere l'elemento successivo.  
  
5. Ricompilare il file VSIX e aprirlo in Esplora risorse per reinstallarlo. Riavviare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
   L'estensione non visibile in Gestione estensioni, ma quando si prova a installarla nuovamente, verrà visualizzato il messaggio seguente: **L'estensione è già installata per tutti i prodotti applicabili.**  
   1. Rimuovere il file di estensione da una sottocartella della *LocalAppData*\Microsoft\VisualStudio\\\Extensions\ [versione]  
  
   - Per visualizzare *LocalAppData*, è necessario impostare cartelle e visualizzare file nascosti nella scheda Visualizza di opzioni cartella Windows Explorer.  
  
   - *LocalAppData* è in genere in C:\Users\\*userName*\AppData\Local\  
  
6. Riavviare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere stereotipi a elementi del modello UML](../modeling/add-stereotypes-to-uml-model-elements.md)   
 [Personalizzare il modello con profili e stereotipi](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Stereotipi standard per modelli UML](../modeling/standard-stereotypes-for-uml-models.md)   
 [Esempio: Colorazione di elementi UML per stereotipo](http://go.microsoft.com/fwlink/?LinkID=213841)   
 [Esempio: Impostazione di stereotipi e profili XSD](http://go.microsoft.com/fwlink/?LinkID=213811)
