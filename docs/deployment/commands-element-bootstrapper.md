---
title: '&lt;I comandi&gt; elemento (programma di avvio automatico) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 785df23b3d76573182eeb97efc5b359e7298a009
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077955"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;I comandi&gt; elemento (programma di avvio automatico)
Il `Commands` elemento implementa test descritti dagli elementi di sotto la `InstallChecks` elemento e dichiara il pacchetto il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bootstrapper deve installare se il test ha esito negativo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## <a name="elements-and-attributes"></a>Gli elementi e attributi  
 Il `Commands` elemento è obbligatorio. L'elemento ha l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Reboot`|Facoltativo. Determina se è necessario riavviare il sistema se uno qualsiasi dei pacchetti di restituire un codice di uscita del riavvio. L'elenco seguente mostra i valori validi:<br /><br /> `Defer`. Il riavvio viene posticipato fino alla fase successiva.<br /><br /> `Immediate`. Causa il riavvio immediato se uno dei pacchetti ha restituito un codice di uscita di riavvio.<br /><br /> `None`. Fa sì che tutte le richieste di riavvio verrà ignorato.<br /><br /> Il valore predefinito è `Immediate`.|  
  
## <a name="command"></a>Comando  
 L'elemento `Command` è un elemento figlio dell'elemento `Commands`. Oggetto `Commands` elemento può avere uno o più `Command` elementi. L'elemento ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`PackageFile`|Obbligatorio. Il nome del pacchetto da installare deve uno o più delle condizioni specificate da `InstallConditions` restituiscono false. Il pacchetto deve essere definito nello stesso file usando un `PackageFile` elemento.|  
|`Arguments`|Facoltativo. Un set di argomenti della riga di comando da passare al file del pacchetto.|  
|`EstimatedInstallSeconds`|Facoltativo. Il tempo stimato, espresso in secondi, necessario per installare il pacchetto. Questo valore determina le dimensioni dell'indicatore di stato che il programma di avvio viene visualizzato all'utente. Il valore predefinito è 0, nel qual caso alcun tempo di stima è specificata.|  
|`EstimatedDiskBytes`|Facoltativo. La quantità stimata di spazio su disco, espressa in byte, che verrà occupata dal pacchetto dopo l'installazione viene completata. Questo valore viene utilizzato in requisiti di spazio su disco rigido che il programma di avvio viene visualizzato all'utente. Il valore predefinito è 0, nel quale caso il programma di bootstrap non visualizza eventuali requisiti di spazio su disco rigido.|  
|`EstimatedTempBytes`|Facoltativo. La quantità stimata di spazio su disco temporaneo, in byte, che richiede il pacchetto.|  
|`Log`|Facoltativo. Il percorso del file di log che genera il pacchetto, relativo alla directory radice del pacchetto.|  
  
## <a name="installconditions"></a>InstallConditions  
 Il `InstallConditions` elemento è figlio di `Command` elemento. Ciascuna `Command` può avere al massimo un elemento `InstallConditions` elemento. Se nessun `InstallConditions` elemento esiste, il pacchetto specificato dal `Condition` verrà sempre eseguito.  
  
## <a name="bypassif"></a>BypassIf  
 Il `BypassIf` elemento è figlio di `InstallConditions` elemento e descrive una condizione positiva in base alle quali non deve essere eseguito il comando. Ciascuna `InstallConditions` può contenere zero o più `BypassIf` elementi.  
  
 `BypassIf` ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Il nome della proprietà da testare. La proprietà deve avere stata precedentemente definita da un elemento figlio del `InstallChecks` elemento. Per altre informazioni, vedere [ \<InstallChecks > elemento](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obbligatorio. Il tipo di confronto da eseguire. L'elenco seguente mostra i valori validi:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obbligatorio. Valore da confrontare con la proprietà.|  
|`Schedule`|Facoltativo. Il nome di un `Schedule` tag che definisce quando questa regola deve essere valutata.|  
  
## <a name="failif"></a>FailIf  
 Il `FailIf` elemento è figlio di `InstallConditions` elemento e descrive una condizione positiva in base alle quali l'installazione deve essere interrotta. Ciascuna `InstallConditions` può contenere zero o più `FailIf` elementi.  
  
 `FailIf` ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Il nome della proprietà da testare. La proprietà deve avere stata precedentemente definita da un elemento figlio del `InstallChecks` elemento. Per altre informazioni, vedere [ \<InstallChecks > elemento](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obbligatorio. Il tipo di confronto da eseguire. L'elenco seguente mostra i valori validi:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obbligatorio. Valore da confrontare con la proprietà.|  
|`String`|Facoltativo. Il testo da visualizzare all'utente in caso di errore.|  
|`Schedule`|Facoltativo. Il nome di un `Schedule` tag che definisce quando questa regola deve essere valutata.|  
  
## <a name="exitcodes"></a>ExitCodes  
 Il `ExitCodes` elemento è figlio di `Command` elemento. Il `ExitCodes` elemento contiene uno o più `ExitCode` elementi, che determinano quali operazioni deve eseguire l'installazione in risposta a un codice di uscita da un pacchetto. Può esistere un facoltativo `ExitCode` elemento sotto un `Command` elemento. `ExitCodes` non ha attributi.  
  
## <a name="exitcode"></a>Codice di uscita  
 Il `ExitCode` elemento è figlio di `ExitCodes` elemento. Il `ExitCode` elemento determina ciò che l'installazione deve eseguire in risposta a un codice di uscita da un pacchetto. `ExitCode` non contiene elementi figlio e ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Value`|Obbligatorio. Il valore del codice di uscita per cui questo `ExitCode` elemento si applica.|  
|`Result`|Obbligatorio. Come l'installazione deve reagire in questo codice di uscita. L'elenco seguente mostra i valori validi:<br /><br /> `Success`. Contrassegna come è stato installato il pacchetto.<br /><br /> `SuccessReboot`. Contrassegna come è stato installato il pacchetto e determina il riavvio del sistema.<br /><br /> `Fail`. Contrassegna il pacchetto come non riuscita.<br /><br /> `FailReboot`. Contrassegna il pacchetto come non superato e determina il riavvio del sistema.|  
|`String`|Facoltativo. Il valore da visualizzare all'utente in risposta a questo codice di uscita.|  
|`FormatMessageFromSystem`|Facoltativo. Determina se utilizzare il messaggio di errore fornita dal sistema corrispondente al codice di uscita oppure utilizzare il valore fornito nel `String`. I valori validi sono `true`, che consente di utilizzare l'errore fornita dal sistema, e `false`, che consente di utilizzare la stringa fornita da `String`. Il valore predefinito è `false`. Se questa proprietà è `false`, ma `String` non è impostato, verrà usato l'errore fornita dal sistema.|  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente definisce i comandi per l'installazione di .NET Framework 2.0.  
  
```xml  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo schema di Product e package](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks > elemento](../deployment/installchecks-element-bootstrapper.md)