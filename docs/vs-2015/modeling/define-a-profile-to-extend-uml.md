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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a495a566f78ceb2b89f8e2070837f038da352a4d
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918871"
---
# <a name="define-a-profile-to-extend-uml"></a>Definire un profilo per estendere UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile definire un *profilo UML* per personalizzare gli elementi del modello standard per scopi specifici. Un profilo definisce uno o più *stereotipi UML*. Uno stereotipo può essere utilizzato per contrassegnare un tipo come rappresentazione di un determinato tipo di oggetto. Uno stereotipo può anche essere usato per estendere l'elenco di proprietà di un elemento.

 Vengono installati diversi profili con le edizioni supportate di Visual Studio. Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). Per altre informazioni su questi profili e su come applicare gli stereotipi, vedere [personalizzare il modello con profili e stereotipi](../modeling/customize-your-model-with-profiles-and-stereotypes.md).

 È possibile definire i propri profili per adattare ed estendere il linguaggio UML alla propria architettura o area aziendale. Ad esempio:

- Se si definiscono spesso siti Web, si può definire un proprio profilo che fornisca uno stereotipo «WebPage» applicabile alle classi nei diagrammi classi. Sarebbe quindi possibile usare i diagrammi classi per pianificare un sito Web. Ogni classe «WebPage» avrebbe proprietà aggiuntive per il contenuto della pagina, lo stile e così via.

- Se si sviluppa software di e-banking, si potrebbe definire un profilo che fornisca uno stereotipo «Account». Sarebbe quindi possibile usare i diagrammi classi per definire tipi diversi di conto e mostrare le relazioni tra di essi.

  È possibile distribuire i propri profili al team. Ogni membro del team può installare il profilo. Ciò consente di modificare e creare modelli che usano i relativi stereotipi.

> [!NOTE]
> Se si applicano gli stereotipi di un profilo in un modello che si sta modificando e quindi si condivide il modello con altre persone, queste devono installare lo stesso profilo nei propri computer. In caso contrario, non saranno in grado di visualizzare gli stereotipi usati.

 Un profilo è spesso parte di un'estensione di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] più grande. Ad esempio, si può definire un comando che traduce alcune parti di un modello in codice. È possibile definire un profilo che gli utenti devono applicare ai pacchetti che vogliono tradurre. È possibile distribuire il nuovo comando insieme al profilo in una singola estensione di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

 È inoltre possibile definire varianti localizzate di un profilo. Gli utenti che caricano l'estensione visualizzano la variante appropriata alle proprie impostazioni cultura.

## <a name="DefineProfile"></a>Come definire un profilo

#### <a name="to-define-a-uml-profile"></a>Per definire un profilo UML

1. Creare un nuovo file XML con l'estensione di file `.profile`.

2. Aggiungere le definizioni dello stereotipo secondo le linee guida descritte nella [struttura di un profilo](#Schema).

3. Aggiungere il profilo a un'estensione di Visual Studio (file `.vsix`). È possibile creare una nuova estensione per il profilo o aggiungere il profilo a un'estensione esistente.

     Vedere la sezione successiva [come aggiungere un profilo a un'estensione di Visual Studio](#AddProfile).

4. Installare l'estensione nel computer.

    1. Fare doppio clic sul file dell'estensione, che ha un'estensione di file `.vsix`.

    2. Riavviare Visual Studio.

5. Verificare che il profilo sia stato installato.

    1. Selezionare il modello in Esplora UML.

    2. Nella Finestra Proprietà fare clic sulla proprietà **profili** . Il profilo verrà visualizzato nel menu. Impostare il segno di spunta accanto al profilo.

    3. Selezionare un elemento per cui il profilo definisce gli stereotipi. Nella Finestra Proprietà fare clic sulla proprietà **stereotipi** . Gli stereotipi verranno visualizzati nell'elenco. Impostare il segno di spunta accanto a uno degli stereotipi.

    4. Se il profilo definisce altre proprietà per questo stereotipo, espandere la proprietà dello stereotipo per visualizzarle.

6. Inviare il file dell'estensione ad altri utenti di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] che lo installeranno nei rispettivi computer.

## <a name="AddProfile"></a>Come aggiungere un profilo a un'estensione di Visual Studio
 Per installare un profilo e poterlo inviare ad altri utenti, è necessario aggiungerlo a un'estensione di Visual Studio. Per ulteriori informazioni, vedere [distribuzione delle estensioni di Visual Studio](https://msdn.microsoft.com/library/dd393694(VS.100).aspx).

#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>Per definire un profilo in una nuova estensione di Visual Studio

1. Creare un progetto di estensione di Visual Studio

   > [!NOTE]
   > È necessario avere installato [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] per usare questa procedura.

   1. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

   2. Nella finestra di dialogo **nuovo progetto** , in **modelli installati**, espandere **oggetto C#visivo** , fare clic su **estendibilità**, quindi fare clic su **progetto VSIX**. Impostare il nome del progetto e fare clic su **OK**.

2. Aggiungere il profilo al progetto.

   - In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto, scegliere **Aggiungi**, quindi fare clic su **elemento esistente**. Nella finestra di dialogo individuare il file del profilo.

3. Imposta la proprietà **copia in output** del file del profilo.

   1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul file del profilo, quindi scegliere **Proprietà**.

   2. Nella Finestra Proprietà impostare la proprietà **copia nella directory di output** su **copia sempre**.

4. In Esplora soluzioni aprire `source.extension.vsixmanifest`.

    Il file viene aperto nell'editor del manifesto dell'estensione.

5. Nella pagina **Asset** aggiungere una riga che descrive il profilo:

   - Fare clic su **Nuovo**. Impostare i campi nella finestra di dialogo **Aggiungi nuovo asset** come indicato di seguito.

   - Imposta il **tipo** su `Microsoft.VisualStudio.UmlProfile`

        Non si tratta di una delle opzioni a discesa. Inserire il nome utilizzando la tastiera.

   - Fare clic **su file in filesystem** e selezionare il nome del file del profilo, ad esempio `MyProfile.profile`

6. Compilazione del progetto.

7. **Per eseguire il debug del profilo**, premere F5.

    Viene aperta un'istanza sperimentale di Visual Studio. In questa istanza aprire un progetto di modellazione. In Esplora modelli UML selezionare l'elemento radice del modello, quindi nella finestra Proprietà selezionare il profilo. Selezionare gli elementi nel modello e impostare gli stereotipi che sono stati definiti per essi.

8. **Per estrarre il progetto VSIX per la distribuzione**

   1. In Esplora risorse aprire la cartella **.\bin\Debug** o **.\bin\Release** per trovare il file con estensione **VSIX** . Si tratta di un file di estensione [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Può essere installato nel computer e inviato ad altri utenti di Visual Studio.

   2. Per installare l'estensione:

       1. Fare doppio clic sul file `.vsix`. Verrà avviato Visual Studio Extension Installer.

       2. Riavviare tutte le istanze di Visual Studio in esecuzione.

   La seguente procedura alternativa può essere usata per estensioni di piccole dimensioni se [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] non è stato installato.

#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>Per definire un'estensione del profilo senza usare Visual Studio SDK

1. Creare una directory di Windows che contiene i tre file seguenti:

    - `.profile` *ProfiloPersonale*

    - `extension.vsixmanifest`

    - `[Content_Types].xml`: digitare questo nome, come illustrato di seguito, con le parentesi quadre

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

     In Esplora risorse, selezionare i tre file, fare clic con il pulsante destro del mouse, scegliere **Invia a**, quindi fare clic su **cartella compressa**.

5. Rinominare il file compresso e cambiare l'estensione di file da `.zip` a `.vsix`.

6. Per installare il profilo in qualsiasi computer con le edizioni appropriate di Visual Studio, fare doppio clic sul file `.vsix`.

#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>Per installare un profilo UML da un'estensione di Visual Studio

1. Fare doppio clic sul file `.vsix` in Esplora risorse o aprirlo in Visual Studio.

2. Fare clic su **Installa** nella finestra di dialogo visualizzata.

3. Per disinstallare o disabilitare temporaneamente l'estensione, aprire **estensioni e aggiornamenti** dal menu **strumenti** .

## <a name="Localized"></a>Come definire i profili localizzati
 È possibile definire profili diversi per impostazioni cultura o lingue diverse e comprimerli tutti nella stessa estensione. Quando un utente carica l'estensione, vedrà il profilo definito per le proprie impostazioni cultura.

 È sempre necessario specificare un profilo predefinito. Se non è stato definito un profilo per le impostazioni cultura dell'utente, verrà visualizzato il profilo predefinito.

#### <a name="to-define-a-localized-profile"></a>Per definire un profilo localizzato

1. Creare un profilo come descritto nelle sezioni precedenti[come definire un profilo](#DefineProfile) e [come aggiungere un profilo a un'estensione di Visual Studio](#AddProfile). Questo è il profilo predefinito e verrà usato in tutte le installazioni per cui non si specifica un profilo localizzato.

2. Aggiungere una nuova directory nella stessa directory del file del profilo predefinito.

    > [!NOTE]
    > Se si sta compilando l'estensione usando un progetto di estensione di Visual Studio, usare Esplora soluzioni per aggiungere una nuova cartella al progetto.

3. Sostituire il nome della nuova directory con il codice breve ISO delle impostazioni cultura localizzate, ad esempio `bg` per il bulgaro o `fr` per il francese. È consigliabile usare un codice indipendente dalle impostazioni cultura, in genere costituito da due lettere, non il codice delle impostazioni cultura specifiche come ad esempio `fr-CA`. Per ulteriori informazioni sui codici delle impostazioni cultura, vedere [Metodo CultureInfo. GetCultures](https://msdn.microsoft.com/library/system.globalization.cultureinfo.getcultures(VS.100).aspx), che fornisce un elenco completo di codici delle impostazioni cultura.

4. Aggiungere una copia del profilo predefinito alla nuova directory. Non modificare il nome file.

     Una cartella di estensione [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] di esempio, prima che venga compilata o compressa in un file di `.vsix`, conterrà le cartelle e i file seguenti:

     `extension.vsixmanifest`

     `MyProfile.profile`

     `fr\MyProfile.profile`

     `de\MyProfile.profile`

    > [!NOTE]
    > Non è necessario inserire in `extension.vsixmanifest` un riferimento alle versioni localizzate dei profili. I file dei profili copiati devono avere lo stesso nome del profilo nella cartella padre.

5. Modificare la nuova copia del profilo, traducendo nella lingua di destinazione tutte le parti che saranno visibili all'utente, ad esempio gli attributi `displayName`.

6. È possibile creare altre cartelle di impostazioni cultura e profili localizzati per tutte le impostazioni cultura desiderate.

7. Compilare l'estensione di Visual Studio, compilando il progetto di estensione o comprimendo tutti i file, come spiegato nelle precedenti sezioni.

## <a name="Schema"></a>Struttura di un profilo

 Per facilitare la modifica dei file di profilo, installare il file `.xsd` in:

 **%Programmi%\Microsoft Visual Studio [versione] \Xml\schemas.**

 Questa sezione usa il profilo C# come esempio. La definizione completa del profilo può essere visualizzata in:

 *unità* **: \Programmi\Microsoft Visual Studio [versione] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\CSharp.profile**

 Le prime parti di questo percorso potrebbero essere diverse nell'installazione in uso.

 Per altre informazioni sul profilo .NET, vedere [stereotipi standard per i modelli UML](../modeling/standard-stereotypes-for-uml-models.md).

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

- `<propertyTypes>`: elenco di tipi usati per le proprietà definite nella sezione stereotipi.

- `<metaclasses>`: elenco di tipi di elementi del modello a cui si applicano gli stereotipi in questo profilo, ad esempio IClass, IInterface, IOperation, IDependency.

- `<stereotypes>`: definizioni dello stereotipo. Ogni definizione include i nomi e i tipi delle proprietà aggiunte all'elemento del modello di destinazione.

#### <a name="property-types"></a>Tipi di proprietà
 La sezione `<propertyTypes>` dichiara un elenco di tipi usati per le proprietà nella sezione `<stereotypes>`. Esistono due tipi di proprietà: esterno ed enumerazione.

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

 Per l'elenco completo dei tipi di elemento del modello e di relazione che è possibile usare come metaclassi, vedere [tipi di elemento del modello](#Elements).

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

 Ogni stereotipo può elencare zero o più proprietà che aggiunge a tutti gli elementi del modello a cui viene applicato. Il `<propertyType>` contiene un collegamento a uno dei tipi definiti nella sezione `<propertyTypes>`. Il collegamento deve essere un oggetto `<externalTypeMoniker>` per fare riferimento a `<externalType>,` o un oggetto `<enumerationTypeMoniker>` per fare riferimento a `<enumerationType>`. Anche in questo caso, il collegamento inizia con il nome del profilo.

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

## <a name="Elements"></a>Tipi di elemento del modello
 Il set di tipi per cui è possibile definire gli stereotipi è elencato in [tipi di elemento del modello UML](../modeling/uml-model-element-types.md).

## <a name="troubleshooting"></a>Risoluzione dei problemi
 Gli stereotipi non vengono visualizzati nei modelli UML.
È necessario selezionare il profilo in un pacchetto o in un modello. Gli stereotipi verranno visualizzati negli elementi all'interno del pacchetto o del modello. Per altre informazioni, vedere [aggiungere stereotipi agli elementi del modello UML](../modeling/add-stereotypes-to-uml-model-elements.md).

 Quando si apre un modello UML, viene visualizzato l'errore seguente: **VS1707: Impossibile caricare i profili seguenti perché si è verificato un errore di serializzazione: profilo. profile**
1. Verificare che la sintassi XML di base del file con estensione profile sia corretta.

2. Assicurarsi che ogni nome di moniker sia nel formato /profileName/nodeName. profileName è il valore dell'attributo name nel nodo del profilo radice. nodeName è il valore dell'attributo name di una metaclasse, externalType o enumerationType.

3. Verificare che la sintassi sia descritta qui e come illustrato in _unità_ **: \Programmi\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\\** .

4. Disinstallare l'estensione errata. Nel menu **Strumenti** fare clic su **Estensioni e aggiornamenti**.

   - Se l'estensione non è visibile, vedere l'elemento successivo.

5. Ricompilare il file VSIX e aprirlo in Esplora risorse per reinstallarlo. Riavvia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

   L'estensione non viene visualizzata in Gestione estensioni, ma quando si tenta di reinstallarla, viene visualizzato il messaggio seguente: **l'estensione è già installata per tutti i prodotti applicabili.**
   1. Rimuovere il file di estensione da una sottocartella di *LocalAppData*\Microsoft\VisualStudio\\[versione] \Extensions\

   - Per visualizzare *LocalAppData*, è necessario impostare Visualizza cartelle e file nascosti nella scheda Visualizza delle opzioni della cartella Esplora risorse.

   - *LocalAppData* è in genere in C:\Users\\*username*\AppData\Local\

6. Riavvia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="see-also"></a>Vedere anche
 [Aggiungere stereotipi agli elementi del modello UML](../modeling/add-stereotypes-to-uml-model-elements.md) [personalizzare il modello con profili e stereotipi](../modeling/customize-your-model-with-profiles-and-stereotypes.md) stereotipi [standard per i modelli UML](../modeling/standard-stereotypes-for-uml-models.md)
 