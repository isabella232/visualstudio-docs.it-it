---
title: Associazione di scelte rapide da tastiera a voci di Menu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 009e9269961b3cd532736fd5b72e28a389a4382a
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220043"
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Associazione di scelte rapide da tastiera a voci di menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per associare un tasto di scelta rapida per un comando di menu personalizzate, è sufficiente aggiungere una voce al file con estensione vsct per il pacchetto. Questo argomento viene illustrato come eseguire il mapping di un tasto di scelta rapida per un pulsante personalizzato, voce di menu o comandi della barra degli strumenti e come applicare il mapping della tastiera nell'editor predefinito o limitati a un editor personalizzato.  
  
 Per assegnare tasti di scelta rapida da tastiera a voci di menu esistenti di Visual Studio, vedere [identificazione e personalizzazione dei tasti](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Scelta di una combinazione di tasti  
 Molti tasti di scelta rapida sono già utilizzati in Visual Studio. È consigliabile non assegnare la stessa combinazione di tasti a più di un comando poiché associazioni duplicate sono difficili da rilevare e possono anche provocare risultati imprevisti. Pertanto, è consigliabile verificare la disponibilità di un collegamento prima di assegnarla.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Per verificare la disponibilità di un tasto di scelta rapida  
  
1. Nel **Strumenti / opzioni / ambiente** finestra, seleziona **tastiera**.  
  
2. Verificare che l'opzione **Usa nuova combinazione in** è impostata su **Global**.  
  
3. Nel **premere i tasti di scelta rapida** , digitare il tasto di scelta rapida che si desidera utilizzare.  
  
    Se il collegamento è già usato in Visual Studio, il **combinazione già utilizzata da** deve essere visualizzato il comando che chiama attualmente lo scelta rapida.  
  
4. Provare diverse combinazioni di tasti per trovarne uno che non è mappata.  
  
   > [!NOTE]
   >  Tasti di scelta rapida che utilizzano ALT possono aprire un menu di scelta e non direttamente eseguire un comando. Pertanto, il **combinazione già utilizzata da** casella può essere vuoto quando si digita un collegamento che include ALT. È possibile verificare che il collegamento non si apre un menu chiudendo il **opzioni** nella finestra di dialogo e quindi premendo i tasti.  
  
   La procedura seguente si presuppone che si dispone di un pacchetto VSPackage esistente con un comando di menu. Se occorre assistenza questa operazione, dare un'occhiata [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Per assegnare un tasto di scelta rapida a un comando  
  
1. Aprire il file con estensione vsct per il pacchetto.  
  
2. Creare un oggetto vuoto `<KeyBindings>` sezione dopo la `<Commands>` se non è già presente.  
  
   > [!WARNING]
   >  Per altre informazioni sui tasti di scelta rapida, vedere [Keybinding](../extensibility/keybinding-element.md).  
  
    Nel `<KeyBindings>` sezione, creare un `<KeyBinding>` voce.  
  
    Impostare il `guid` e `id` attributi a quelle del comando da richiamare.  
  
    Impostare il `mod1` dell'attributo **controllo**, **Alt**, oppure **MAIUSC**.  
  
    La sezione di tasti di scelta rapida dovrebbe essere simile al seguente:  
  
   ```xml  
   <KeyBindings>  
       <KeyBinding guid="<name of command set>" id="<name of command id>"  
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
   </KeyBindings>  
  
   ```  
  
   Se il tasto di scelta rapida richiede più di due chiavi, impostare il `mod2` e `key2` attributi.  
  
   Nella maggior parte delle situazioni **MAIUSC** non deve essere utilizzato senza un modificatore secondo quanto ci si già fa sì che la maggior parte dei tasti alfanumerici in cui digitare una lettera maiuscola o un simbolo.  
  
   Codici di tasti virtuali permettono di accedere tasti speciali che non è un carattere associato, ad esempio, le chiavi di funzione e il **BACKSPACE** chiave. Per altre informazioni, vedere [codici tasto virtuale](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
   Per rendere disponibile il comando in Visual Studio editor, impostare il `editor` dell'attributo `guidVSStd97`.  
  
   Per rendere il comando è disponibile solo in un editor personalizzato, impostare il `editor` dell'attributo per il nome dell'editor personalizzato che è stato generato dal [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modello di pacchetto durante la creazione di VSPackage che include l'editor personalizzato. Per trovare il valore del nome, esaminare i `<Symbols>` sezione per un `<GuidSymbol>` nodo il cui `name` attributo termina con "`editorfactory`." Si tratta del nome dell'editor personalizzato.  
  
## <a name="example"></a>Esempio  
 Questo esempio associa il tasto di scelta rapida CTRL + ALT + C per un comando denominato `cmdidMyCommand` in un pacchetto denominato `MyPackage`.  
  
```  
<CommandTable>  
. . .  
<Commands>  
. . .  
</Commands>  
<KeyBindings>  
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"   
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />  
</KeyBindings>  
. . .  
</CommandTable>  
```  
  
## <a name="example"></a>Esempio  
 Questo esempio associa il tasto di scelta rapida CTRL + B per un comando denominato `cmdidBold` in un progetto denominato `TestEditor`. Il comando è disponibile solo nell'editor personalizzato e non in altri editor.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)

