---
title: Associazione dei tasti di scelta rapida alle voci di menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e362a61c5ecab78c332eb5e077a02ee4e9e3fa9b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295623"
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Associazione di scelte rapide da tastiera a voci di menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per associare un tasto di scelta rapida a un comando di menu personalizzato, è sufficiente aggiungere una voce al file con estensione vsct per il pacchetto. In questo argomento viene illustrato come eseguire il mapping di una scelta rapida da tastiera a un pulsante personalizzato, una voce di menu o un comando della barra degli strumenti e come applicare il mapping della tastiera nell'editor predefinito o come limitarlo a un editor personalizzato.  
  
 Per assegnare tasti di scelta rapida alle voci di menu di Visual Studio esistenti, vedere [identificazione e personalizzazione dei tasti di scelta rapida](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Scelta di una combinazione di tasti  
 Molti tasti di scelta rapida sono già in uso in Visual Studio. Non è consigliabile assegnare lo stesso collegamento a più di un comando perché le associazioni duplicate sono difficili da rilevare e potrebbero anche causare risultati imprevedibili. Pertanto, è consigliabile verificare la disponibilità di un collegamento prima di assegnarlo.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Per verificare la disponibilità di un tasto di scelta rapida  
  
1. Nella finestra **strumenti/opzioni/ambiente** selezionare **tastiera**.  
  
2. Assicurarsi che **Usa nuovo collegamento in** sia impostato su **globale**.  
  
3. Nella casella **premere i tasti di scelta rapida** Digitare il tasto di scelta rapida che si desidera utilizzare.  
  
    Se il tasto di scelta rapida è già usato in Visual Studio, il **collegamento attualmente usato da** box visualizzerà il comando attualmente chiamato dal collegamento.  
  
4. Provare combinazioni diverse di chiavi finché non ne viene individuato uno non mappato.  
  
   > [!NOTE]
   > Le scelte rapide da tastiera che usano ALT possono aprire un menu e non eseguire direttamente un comando. Pertanto, il **collegamento attualmente utilizzato da** box può essere vuoto quando si digita un tasto di scelta rapida che include alt. È possibile verificare che il collegamento non apra un menu chiudendo la finestra di dialogo **Opzioni** e quindi premendo i tasti.  
  
   Nella procedura seguente si presuppone che si disponga di un VSPackage esistente con un comando di menu. Per ottenere assistenza, vedere [creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Per assegnare un tasto di scelta rapida a un comando  
  
1. Aprire il file con estensione vsct per il pacchetto.  
  
2. Crea una sezione di `<KeyBindings>` vuota dopo l'`<Commands>` se non è già presente.  
  
   > [!WARNING]
   > Per ulteriori informazioni sui tasti di scelta, vedere la pagina relativa all' [associazione](../extensibility/keybinding-element.md)di tasti.  
  
    Nella sezione `<KeyBindings>` creare una voce di `<KeyBinding>`.  
  
    Impostare gli attributi `guid` e `id` su quelli del comando che si desidera richiamare.  
  
    Impostare l'attributo `mod1` per **controllare**, **ALT**o **MAIUSC**.  
  
    La sezione delle combinazioni di tasti dovrebbe avere un aspetto simile al seguente:  
  
   ```xml  
   <KeyBindings>  
       <KeyBinding guid="<name of command set>" id="<name of command id>"  
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
   </KeyBindings>  
  
   ```  
  
   Se il tasto di scelta rapida richiede più di due chiavi, impostare gli attributi `mod2` e `key2`.  
  
   Nella maggior parte dei casi, lo **spostamento** non deve essere usato senza un secondo modificatore perché la pressione della maggior parte delle chiavi alfanumeriche consente di digitare una lettera maiuscola o un simbolo.  
  
   I codici a chiave virtuale consentono di accedere a tasti speciali a cui non è associato alcun carattere, ad esempio i tasti funzione e il tasto **BACKSPACE** . Per ulteriori informazioni, vedere [codici chiave virtuale](https://go.microsoft.com/fwlink/?LinkID=105932).  
  
   Per rendere il comando disponibile nell'editor di Visual Studio, impostare l'attributo `editor` su `guidVSStd97`.  
  
   Per rendere il comando disponibile solo in un editor personalizzato, impostare l'attributo `editor` sul nome dell'editor personalizzato generato dal modello di pacchetto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] quando è stato creato il pacchetto VSPackage che include l'editor personalizzato. Per trovare il valore del nome, esaminare la sezione `<Symbols>` per un nodo `<GuidSymbol>` il cui attributo `name` termina con "`editorfactory`". Si tratta del nome dell'editor personalizzato.  
  
## <a name="example"></a>Esempio  
 In questo esempio il tasto di scelta rapida CTRL + ALT + C viene associato a un comando denominato `cmdidMyCommand` in un pacchetto denominato `MyPackage`.  
  
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
 In questo esempio il tasto di scelta rapida CTRL + B viene associato a un comando denominato `cmdidBold` in un progetto denominato `TestEditor`. Il comando è disponibile solo nell'editor personalizzato e non in altri editor.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)
