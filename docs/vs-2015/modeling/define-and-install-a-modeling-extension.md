---
title: Definire e installare un'estensione di modellazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: 82a58dc5-c7cf-4521-a6da-7ff09cd0de9d
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c38150dd84ef8898b2aa894a614dfb79e289b593
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850457"
---
# <a name="define-and-install-a-modeling-extension"></a>Definire e installare un'estensione di modellazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, è possibile definire le estensioni ai diagrammi di modellazione. In questo modo, è possibile adattare i modelli e diagrammi alle proprie esigenze. Ad esempio, è possibile definire comandi di menu, profili UML, vincoli di convalida ed elementi della casella degli strumenti. È possibile definire diversi componenti in un'unica estensione. È anche possibile distribuire queste estensioni ad altri utenti di Visual Studio in formato [VSIX (Visual Studio Integration Extension)](https://msdn.microsoft.com/library/dd393694(VS.100).aspx). È possibile creare un'estensione VSIX tramite un progetto VSIX in Visual Studio.

## <a name="requirements"></a>Requisiti di
 Vedere [Requisiti](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="creating-a-modeling-extension-solution"></a>Creazione di una soluzione di estensione di modellazione
 Per definire un'estensione di modellazione, è necessario creare una soluzione contenente questi progetti:

- Un progetto VSIX ( [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Integration Extension), che genera un file che funge da programma di installazione per i componenti dell'estensione.

- Un progetto di libreria di classi, necessario per i componenti che includono il codice programma.

  Se si vuole creare un'estensione con diversi componenti, è possibile svilupparli in un'unica soluzione. È necessario un solo progetto VSIX.

  I componenti che non richiedono codice, ad esempio gli elementi della casella degli strumenti personalizzati e i profili UML personalizzati, possono essere aggiunti direttamente al progetto VSIX senza usare progetti di libreria di classi separati. I componenti che richiedono il codice programma si definiscono più facilmente in un progetto di libreria di classi separato. I componenti che richiedono il codice includono i gestori di movimento, i comandi di menu e il codice di convalida.

#### <a name="to-create-a-class-library-project-for-menu-commands-gesture-handlers-or-validation"></a>Per creare un progetto di libreria di classi per comandi di menu, gestori di movimento o convalida

1. Nel menu **File** , scegliere **Nuovo**, **Progetto**.

2. In **Modelli installati**selezionare **Visual C#** o **Visual Basic**, quindi scegliere **Libreria di classi**.

#### <a name="to-create-a-vsix-project"></a>Per creare un progetto VSIX

1. Se si sta creando un componente con il codice, è più facile creare prima il progetto di libreria di classi e aggiungere poi il codice al progetto.

2. Creare un progetto VSIX.

    1. In **Esplora soluzioni**scegliere **Aggiungi**, **Nuovo progetto**dal menu di scelta rapida della soluzione.

    2. In **Modelli installati**espandere **Visual C#** o **Visual Basic**, quindi selezionare **Extensibility**. Nella colonna centrale scegliere **Progetto VSIX**.

3. Impostare il progetto VSIX come progetto di avvio della soluzione.

    - In Esplora soluzioni scegliere **Imposta come progetto di avvio**dal menu di scelta rapida del progetto VSIX.

4. Aprire **source.extension.vsixmanifest**. Il file viene aperto nell'editor del manifesto.

5. Nella scheda **Metadati** impostare i campi del nome e della descrizione di VSIX.

6. Nella scheda **Destinazioni di installazione** scegliere **Nuovo** e impostare le versioni di Visual Studio come destinazioni.

7. Nella scheda **Asset** aggiungere i componenti all'estensione di Visual Studio.

    1. Scegliere **Nuovo**.

    2. Per un componente con il codice, impostare questi campi nella finestra di dialogo **Aggiungi nuovo asset** :

        |||
        |-|-|
        |**Tipo** =|**Microsoft.VisualStudio.MefComponent**|
        |**Source** =|**Progetto nella soluzione corrente**|
        |**Project** =|*Progetto di libreria di classi*|
        |**Incorpora in questa cartella** =|*(empty)*|

         Per altri tipi di componente, vedere i collegamenti nella sezione successiva.

## <a name="developing-the-component"></a>Sviluppo del componente
 Per ogni componente come i comandi di menu o i gestori di movimento, è necessario definire un gestore separato. È possibile inserire diversi gestori nello stesso progetto di libreria di classi. La tabella seguente riepiloga i diversi tipi di gestore.

|Tipo di estensione|Argomento|Modo in cui viene di solito dichiarato ogni componente|
|--------------------|-----------|----------------------------------------------|
|Comando di menu|[Definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(ICommandExtension))]`<br /><br /> `public class MyCommand : ICommandExtension`<br /><br /> `{...`|
|Trascinamento della selezione o doppio clic|[Definire un gestore modelli in un diagramma di modellazione](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(IGestureExtension))]`<br /><br /> `public class MyGesture : IGestureExtension`<br /><br /> `{...`|
|Vincolo di convalida|[Definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md)|`[Export(typeof(     System.Action<ValidationContext, object>))]`<br /><br /> `[ValidationMethod(ValidationCategories.Save`<br /><br /> `&#124; ValidationCategories.Menu)]`<br /><br /> `public void ValidateSomething`<br /><br /> `(ValidationContext context, IClassifier elementToValidate)`<br /><br /> `{...}`|
|Gestore eventi per il collegamento dell'elemento di lavoro|[Definire un gestore dei collegamenti agli elementi di lavoro](../modeling/define-a-work-item-link-handler.md)|`[Export(typeof(ILinkedWorkItemExtension))]`<br /><br /> `public class MyWorkItemEventHandler : ILinkedWorkItemExtension`<br /><br /> `{...`|
|Profilo UML|[Definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md)|(Da definire)|
|Elemento della Casella degli strumenti|[Definire un elemento della casella degli strumenti di modellazione personalizzata](../modeling/define-a-custom-modeling-toolbox-item.md)|(Da definire)|

## <a name="running-an-extension-during-its-development"></a>Esecuzione di un'estensione durante lo sviluppo

#### <a name="to-run-an-extension-during-its-development"></a>Per eseguire un'estensione durante lo sviluppo

1. Scegliere **Avvia debug**dal menu **debug** [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

     Il progetto viene compilato e viene avviata una nuova istanza di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] in modalità sperimentale.

    - In alternativa è possibile scegliere **Avvia senza eseguire debug**, che riduce il tempo impiegato per avviare il programma.

2. Creare o aprire un progetto di modellazione nell'istanza sperimentale di Visual Studio e creare o aprire un diagramma.

     L'estensione verrà caricata ed eseguita.

3. Se è stato selezionato **Avvia senza eseguire il debug** , ma si vuole usare il debugger, tornare all'istanza principale di Visual Studio. Scegliere **Connetti a processo** dal menu **Debug**. Nella finestra di dialogo selezionare l'istanza sperimentale di Visual Studio, con il nome programma **devenv**.

## <a name="Installing"></a>Installazione e disinstallazione di un'estensione
 Seguire questa procedura per eseguire l'estensione nell'istanza principale di Visual Studio nel proprio computer o in altri.

1. Nel computer trovare il file **.vsix** compilato dal progetto di estensione.

    1. In **Esplora soluzioni**scegliere **Apri cartella in Esplora risorse**dal menu di scelta rapida del progetto.

    2. Individuare il file **bin\\\*\\** _progettoutente_ **. vsix**

2. Copiare il file **.vsix** nel computer di destinazione in cui si vuole installare l'estensione. Può trattarsi del computer in uso o di un altro computer.

    - Nel computer di destinazione deve essere installata una delle edizioni di Visual Studio specificate nella scheda **Destinazione installazione** di **source.extension.vsixmanifest**.

3. Nel computer di destinazione aprire il file **.vsix** , ad esempio facendovi doppio clic.

     **Visual Studio Extension Installer** si apre e installa l'estensione.

4. Avviare o riavviare Visual Studio.

#### <a name="to-uninstall-an-extension"></a>Per disinstallare un'estensione

1. Nel menu **Strumenti** fare clic su **Estensioni e aggiornamenti**.

2. Espandere **Estensioni installate**.

3. Selezionare l'estensione e quindi fare clic su **Disinstalla**.

   Raramente, un'estensione errata non viene caricata e crea un report nella finestra degli errori, ma non viene visualizzata in Gestione estensioni. In tal caso, è possibile rimuovere l'estensione eliminando il file dal percorso seguente, in cui *% LocalAppData%* è in genere *driveName*: \Users\\*username*\AppData\Local:

   *% LocalAppData%* **\Microsoft\VisualStudio\\[versione] \Extensions**

## <a name="see-also"></a>Vedere anche
 [Definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md) [definire un elemento della casella degli strumenti di modellazione personalizzata](../modeling/define-a-custom-modeling-toolbox-item.md) [definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md) [definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
