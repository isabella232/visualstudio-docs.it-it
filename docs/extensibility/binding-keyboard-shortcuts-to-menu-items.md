---
title: Associazione di scelte rapide da tastiera a voci di Menu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d319dfdf1203870ecc1b80787522a56d6f37b5e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940375"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Eseguire l'associazione di scelte rapide da tastiera a voci di menu
Per associare un tasto di scelta rapida per un comando di menu personalizzate, è sufficiente aggiungere una voce per il *vsct* file per il pacchetto. Questo argomento viene illustrato come eseguire il mapping di un tasto di scelta rapida per un pulsante personalizzato, voce di menu o comandi della barra degli strumenti e come applicare il mapping della tastiera nell'editor predefinito o limitati a un editor personalizzato.  
  
 Per assegnare tasti di scelta rapida da tastiera a voci di menu esistenti di Visual Studio, vedere [identificare e personalizzare i tasti di scelta rapida](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choose-a-key-combination"></a>Scegliere una combinazione di tasti  
 Molti tasti di scelta rapida sono già utilizzati in Visual Studio. È consigliabile non assegnare la stessa combinazione di tasti a più di un comando poiché associazioni duplicate sono difficili da rilevare e possono anche provocare risultati imprevisti. Pertanto, è consigliabile verificare la disponibilità di un collegamento prima di assegnarla.  
  
### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Per verificare la disponibilità di un tasto di scelta rapida  
  
1. Nel **degli strumenti** > **opzioni** > **ambiente** finestra selezionare **tastiera**.  
  
2. Verificare che l'opzione **Usa nuova combinazione in** è impostata su **Global**.  
  
3. Nel **premere i tasti di scelta rapida** , digitare il tasto di scelta rapida che si desidera utilizzare.  
  
    Se il collegamento è già usato in Visual Studio, il **combinazione già utilizzata da** deve essere visualizzato il comando che chiama attualmente lo scelta rapida.  
  
4. Provare diverse combinazioni di tasti per trovarne uno che non è mappata.  
  
   > [!NOTE]
   >  Tasti di scelta rapida che usano **Alt** può aprire un menu di scelta e non direttamente eseguire un comando. Pertanto, il **combinazione già utilizzata da** casella può essere vuoto quando si digita un collegamento che include **Alt**. È possibile verificare che il collegamento non si apre un menu chiudendo il **opzioni** nella finestra di dialogo e quindi premendo i tasti.  
  
   La procedura seguente si presuppone che si dispone di un pacchetto VSPackage esistente con un comando di menu. Se occorre assistenza questa operazione, dare un'occhiata [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Per assegnare un tasto di scelta rapida a un comando  
  
1. Aprire il *vsct* file per il pacchetto.  
  
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
  
   Codici di tasti virtuali permettono di accedere tasti speciali che non è un carattere associato, ad esempio, le chiavi di funzione e il **Backspace** chiave. Per altre informazioni, vedere [codici tasto virtuale](https://docs.microsoft.com/windows/desktop/inputdev/virtual-key-codes).  
  
   Per rendere disponibile il comando in Visual Studio editor, impostare il `editor` dell'attributo `guidVSStd97`.  
  
   Per rendere il comando è disponibile solo in un editor personalizzato, impostare il `editor` dell'attributo per il nome dell'editor personalizzato che è stato generato dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modello di pacchetto durante la creazione di VSPackage che include l'editor personalizzato. Per trovare il valore del nome, esaminare i `<Symbols>` sezione per un `<GuidSymbol>` nodo il cui `name` attributo termina con "`editorfactory`." Si tratta del nome dell'editor personalizzato.  
  
## <a name="example"></a>Esempio  
 Questo esempio associa il tasto di scelta rapida **Ctrl**+**Alt**+**C** a un comando denominato `cmdidMyCommand` in un pacchetto denominato `MyPackage`.  
  
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
 Questo esempio associa il tasto di scelta rapida **Ctrl**+**B** a un comando denominato `cmdidBold` in un progetto denominato `TestEditor`. Il comando è disponibile solo nell'editor personalizzato e non in altri editor.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)