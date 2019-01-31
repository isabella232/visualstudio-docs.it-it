---
title: Gestione delle impostazioni di un'applicazione (.NET)| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
ms.assetid: 35254321-ad14-47d9-b8c6-39ab3203c5d9
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a2d5d5ff514752234bba3020927716d57ee413d1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793286"
---
# <a name="managing-application-settings-net"></a>Gestione delle impostazioni di un'applicazione (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le impostazioni dell'applicazione consentono di archiviare le informazioni sull'applicazione in modo dinamico. Le impostazioni consentono di archiviare nel computer client le informazioni che non devono essere incluse nel codice dell'applicazione (ad esempio una stringa di connessione), le preferenze dell'utente e altre informazioni necessarie in fase di esecuzione.  
  
 Le impostazioni dell'applicazione sostituiscono le proprietà dinamiche usate nelle versioni precedenti di Visual Studio.  
  
 Ogni impostazione dell'applicazione deve avere un nome univoco. Tale nome può essere formato da una combinazione di lettere, numeri o un carattere di sottolineatura, non può iniziare con un numero e non può contenere spazi. Il nome può essere modificato tramite la proprietà `Name` .  
  
 Le impostazioni dell'applicazione possono essere archiviate come qualsiasi tipo di dati che può essere serializzato come XML che abbia un oggetto `TypeConverter` che implementa `ToString`/`FromString`. I tipi più comuni sono `String`, `Integer`e `Boolean`, ma è anche possibile archiviare i valori come <xref:System.Drawing.Color>, <xref:System.Object>o come una stringa di connessione.  
  
 Anche le impostazioni dell'applicazione contengono un valore. Il valore viene impostato con la proprietà **Valore** e deve corrispondere al tipo di dati dell'impostazione.  
  
 Inoltre, in fase di progettazione, è possibile associare le impostazioni dell'applicazione alla proprietà di un form o di un controllo.  
  
 Sono disponibili due tipi di impostazioni dell'applicazione, in base all'ambito:  
  
- Le impostazioni con ambito di applicazione possono essere usate per informazioni quali un URL per un servizio Web o una stringa di connessione del database. Questi valori sono associati all'applicazione. Di conseguenza, gli utenti non possono modificarli in fase di esecuzione.  
  
- Le impostazioni con ambito di utente possono essere usate per informazioni quali la memorizzazione dell'ultima posizione di un form oppure una preferenza su un tipo di carattere. Gli utenti possono modificare questi valori in fase di esecuzione.  
  
  È possibile modificare il tipo di un'impostazione usando la proprietà **Ambito** .  
  
  Nel sistema del progetto le impostazioni dell'applicazione vengono archiviate in due file XML: un file app.config, creato in fase di progettazione al momento della creazione della prima impostazione dell'applicazione, e un file user.config, creato in fase di esecuzione quando l'utente che esegue l'applicazione modifica il valore di una qualsiasi impostazione utente. Le modifiche apportate alle impostazioni utente non vengono scritte su disco a meno che nell'applicazione non venga specificamente chiamato un metodo che esegua questa operazione.  
  
## <a name="creating-application-settings-at-design-time"></a>Creazione di impostazioni dell'applicazione in fase di progettazione  
 In fase di progettazione, le impostazioni dell'applicazione possono essere create in due modi, mediante la pagina **Impostazioni** di **Creazione progetti**oppure mediante la finestra **Proprietà** per un form o un controllo, che consente di associare un'impostazione direttamente a una proprietà.  
  
 Quando si crea un'impostazione con ambito di applicazione, ad esempio una stringa di connessione del database oppure un riferimento a risorse del server, in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tale impostazione viene salvata nel file app.config con il tag `<applicationSettings>` . (Le stringhe di connessione vengono salvate nel tag `<connectionStrings>` .)  
  
 Quando si crea un'impostazione con ambito di utente, ad esempio il tipo di carattere predefinito, la pagina iniziale o le dimensioni delle finestre, in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tale impostazione viene salvata nel file app.config con il tag `<userSettings>` .  
  
> [!IMPORTANT]
>  Quando si archiviano stringhe di connessione in app.config, è opportuno adottare delle precauzioni per evitare di rivelare informazioni riservate, quali password o percorsi del server, nella stringa di connessione.  
>   
>  Se si ricevono informazioni della stringa di connessione da un'origine esterna, quale un utente che immette un ID utente e una password, accertarsi che tra i valori usati per costruire la stringa di connessione non siano presenti parametri aggiuntivi in grado di modificare il comportamento della connessione.  
>   
>  Valutare l'uso della funzionalità di configurazione protetta per crittografare le informazioni riservate nel file di configurazione. Per altre informazioni, vedere [Protezione delle informazioni di connessione](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
> [!NOTE]
>  Poiché non è presente alcun modello di file di configurazione per le librerie di classi, le impostazioni dell'applicazione non si applicano ai progetti Libreria di classi, ad eccezione dei progetti DLL di Visual Studio Tools per Office che possono avere un file di configurazione.  
  
## <a name="using-customized-settings-files"></a>Uso di file di impostazioni personalizzati  
 È possibile aggiungere file di impostazioni personalizzati al progetto per agevolare la gestione dei gruppi di impostazioni. Le impostazioni contenute in un unico file vengono caricate e salvate come unità. Di conseguenza, l'archiviazione delle impostazioni in file diversi per i gruppi di utilizzo frequente e di utilizzo non frequente può determinare un risparmio di tempo nel caricamento e nel salvataggio delle impostazioni.  
  
 Ad esempio, è possibile aggiungere un file quale SpecialSettings.settings al progetto. Mentre la classe `SpecialSettings` non è esposta nello spazio dei nomi `My` , **Visualizza codice** può leggere il file di impostazioni personalizzate contenente `Partial Class SpecialSettings`.  
  
 Progettazione impostazioni cerca innanzi tutto il file Settings.settings creato dal sistema del progetto, ovvero il file predefinito visualizzato nella scheda **Impostazioni** di Creazione progetti. Settings.settings è situato nella cartella Progetti per i progetti [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] e nella cartella Proprietà per i progetti [!INCLUDE[csprcs](../includes/csprcs-md.md)] . Successivamente, Creazione progetti cerca gli altri file di impostazioni nella cartella radice del progetto. Pertanto, è necessario inserirvi il file di impostazioni personalizzato. Se si aggiunge un file .settings in un altro punto del progetto, questo non verrà trovato da Creazione progetti.  
  
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-basic"></a>Accesso o modifica delle impostazioni dell'applicazione in fase di esecuzione in Visual Basic  
 Nei progetti [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] è possibile accedere alle impostazioni dell'applicazione in fase di esecuzione usando l'oggetto `My.Settings` . Nella pagina **Impostazioni** scegliere il pulsante **Visualizza codice** per visualizzare il file Settings.vb. Nel file Settings.vb viene definita la classe `Settings` che consente di gestire i seguenti eventi nella classe delle impostazioni: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>e <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. La classe `Settings` nel file Settings.vb è una classe parziale in cui viene visualizzato solo il codice di proprietà dell'utente, non l'intera classe generata. Per altre informazioni sull'accesso alle impostazioni dell'applicazione mediante l'oggetto `My.Settings` , vedere [Accessing Application Settings](http://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e).  
  
 I valori di qualsiasi impostazione con ambito di utente che vengono modificati dall'utente in fase di esecuzione, ad esempio la posizione di un form, vengono archiviati in un file user.config. I valori predefiniti vengono salvati nel file app.config.  
  
 Se si modifica qualsiasi impostazione con ambito di utente in fase di esecuzione, ad esempio durante il test dell'applicazione, e si desidera ripristinare i valori predefiniti per queste impostazioni, scegliere il pulsante **Sincronizza** .  
  
 È consigliabile usare l'oggetto `My.Settings` e il file .settings predefinito per accedere alle impostazioni. Ciò perché è possibile usare Progettazione impostazioni per assegnare proprietà alle impostazioni e le impostazioni utente vengono salvate automaticamente prima della chiusura dell'applicazione. L'applicazione [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , comunque, può accedere direttamente alle impostazioni. In quel caso è necessario accedere alla classe `MySettings` e usare un file .settings personalizzato nella radice del progetto. È inoltre necessario salvare le impostazioni utente prima di terminare l'applicazione, come per le applicazioni C#, come illustrato nella sezione seguente.  
  
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-c"></a>Accesso o modifica delle impostazioni dell'applicazione in fase di esecuzione in Visual C#  
 In linguaggi diversi da [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], quali [!INCLUDE[csprcs](../includes/csprcs-md.md)], è necessario accedere direttamente alla classe `Settings` , come illustrato nell'esempio seguente relativo a [!INCLUDE[csprcs](../includes/csprcs-md.md)] .  
  
```csharp  
Properties.Settings.Default.FirstUserSetting = "abc";  
```  
  
 È inoltre necessario chiamare in modo esplicito il metodo `Save` di questa classe wrapper per rendere persistenti le impostazioni utente. Questa operazione viene generalmente effettuata nel gestore eventi `Closing` del form principale. Nell'esempio seguente relativo a [!INCLUDE[csprcs](../includes/csprcs-md.md)] viene illustrata una chiamata al metodo `Save` .  
  
```csharp  
Properties.Settings.Default.Save();  
```  
  
 Per informazioni generali sull'accesso alle impostazioni dell'applicazione mediante la classe `Settings`, vedere [Cenni preliminari sulle impostazioni delle applicazioni](http://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc). Per impostazioni sullo scorrimento delle impostazioni, vedere questo [post del forum](http://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso alle impostazioni dell'applicazione](http://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e)
