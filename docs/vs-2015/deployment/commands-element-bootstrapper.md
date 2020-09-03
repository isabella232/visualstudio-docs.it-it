---
title: '&lt;Elemento Commands &gt; (programma di avvio automatico) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af10c9e0b26a6ef2c8e7a98bc345b8e86017682b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205339"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Elemento Commands &gt; (programma di avvio automatico)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L' `Commands` elemento implementa i test descritti dagli elementi al di sotto dell' `InstallChecks` elemento e dichiara il pacchetto che [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] deve essere installato dal programma di avvio automatico in caso di esito negativo del test.  
  
## <a name="syntax"></a>Sintassi  
  
```  
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
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L' `Commands` elemento è obbligatorio. L'elemento presenta l'attributo seguente:  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Reboot`|Facoltativa. Determina se il sistema deve essere riavviato se uno dei pacchetti restituisce un codice di uscita del riavvio. Nell'elenco seguente sono riportati i valori validi:<br /><br /> `Defer`. Il riavvio viene posticipato fino a un momento successivo.<br /><br /> `Immediate`. Causa un riavvio immediato se uno dei pacchetti ha restituito un codice di uscita di riavvio.<br /><br /> `None`. Consente di ignorare tutte le richieste di riavvio.<br /><br /> Il valore predefinito è `Immediate`.|  
  
## <a name="command"></a>Comando  
 L'elemento `Command` è un elemento figlio dell'elemento `Commands`. Un `Commands` elemento può contenere uno o più `Command` elementi. L'elemento presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`PackageFile`|Obbligatorio. Il nome del pacchetto da installare deve avere una o più condizioni specificate da `InstallConditions` return false. Il pacchetto deve essere definito nello stesso file utilizzando un `PackageFile` elemento.|  
|`Arguments`|facoltativo. Set di argomenti della riga di comando da passare al file del pacchetto.|  
|`EstimatedInstallSeconds`|facoltativo. Tempo stimato, in secondi, necessario per installare il pacchetto. Questo valore determina le dimensioni dell'indicatore di stato che il programma di avvio automatico Visualizza all'utente. Il valore predefinito è 0, nel qual caso non viene specificata alcuna stima temporale.|  
|`EstimatedDiskBytes`|facoltativo. Quantità stimata di spazio su disco, in byte, che il pacchetto occuperà al termine dell'installazione. Questo valore viene utilizzato nei requisiti di spazio su disco rigido che il programma di avvio automatico Visualizza all'utente. Il valore predefinito è 0, nel qual caso il programma di avvio automatico non Visualizza i requisiti di spazio su disco rigido.|  
|`EstimatedTempBytes`|facoltativo. Quantità stimata di spazio su disco temporaneo, in byte, necessaria per il pacchetto.|  
|`Log`|facoltativo. Percorso del file di log generato dal pacchetto, relativo alla directory radice del pacchetto.|  
  
## <a name="installconditions"></a>InstallConditions  
 L' `InstallConditions` elemento è un elemento figlio dell' `Command` elemento. Ogni `Command` elemento può contenere al massimo un `InstallConditions` elemento. Se non `InstallConditions` esiste alcun elemento, il pacchetto specificato da `Condition` viene sempre eseguito.  
  
## <a name="bypassif"></a>BypassIf  
 L' `BypassIf` elemento è un elemento figlio dell' `InstallConditions` elemento e descrive una condizione positiva con cui il comando non deve essere eseguito. Ogni `InstallConditions` elemento può contenere zero o più `BypassIf` elementi.  
  
 `BypassIf` ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Nome della proprietà da testare. La proprietà deve essere stata definita in precedenza da un figlio dell' `InstallChecks` elemento. Per ulteriori informazioni, vedere [ \<InstallChecks> elemento](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obbligatorio. Tipo di confronto da eseguire. Nell'elenco seguente sono riportati i valori validi:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obbligatorio. Valore da confrontare con la proprietà.|  
|`Schedule`|facoltativo. Nome di un `Schedule` tag che definisce quando valutare la regola.|  
  
## <a name="failif"></a>FailIf  
 L' `FailIf` elemento è un elemento figlio dell' `InstallConditions` elemento e descrive una condizione positiva in base alla quale deve essere arrestata l'installazione. Ogni `InstallConditions` elemento può contenere zero o più `FailIf` elementi.  
  
 `FailIf` ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Nome della proprietà da testare. La proprietà deve essere stata definita in precedenza da un figlio dell' `InstallChecks` elemento. Per ulteriori informazioni, vedere [ \<InstallChecks> elemento](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obbligatorio. Tipo di confronto da eseguire. Nell'elenco seguente sono riportati i valori validi:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obbligatorio. Valore da confrontare con la proprietà.|  
|`String`|facoltativo. Testo da visualizzare all'utente in caso di errore.|  
|`Schedule`|facoltativo. Nome di un `Schedule` tag che definisce quando valutare la regola.|  
  
## <a name="exitcodes"></a>ExitCodes  
 L' `ExitCodes` elemento è un elemento figlio dell' `Command` elemento. L' `ExitCodes` elemento contiene uno o più `ExitCode` elementi, che determinano le operazioni che l'installazione deve eseguire in risposta a un codice di uscita da un pacchetto. Può essere presente un `ExitCode` elemento facoltativo sotto un `Command` elemento. L'elemento `ExitCodes` non ha attributi.  
  
## <a name="exitcode"></a>ExitCode  
 L' `ExitCode` elemento è un elemento figlio dell' `ExitCodes` elemento. L' `ExitCode` elemento determina l'operazione che deve essere eseguita dall'installazione in risposta a un codice di uscita da un pacchetto. `ExitCode` non contiene elementi figlio e ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Value`|Obbligatorio. Valore del codice di uscita a cui `ExitCode` si applica questo elemento.|  
|`Result`|Obbligatorio. Il modo in cui l'installazione deve rispondere a questo codice di uscita. Nell'elenco seguente sono riportati i valori validi:<br /><br /> `Success`. Contrassegna il pacchetto come installato correttamente.<br /><br /> `SuccessReboot`. Contrassegna il pacchetto come installato correttamente e indica al sistema di eseguire il riavvio.<br /><br /> `Fail`. Contrassegna il pacchetto come non riuscito.<br /><br /> `FailReboot`. Contrassegna il pacchetto come non riuscito e indica al sistema di eseguire il riavvio.|  
|`String`|facoltativo. Valore da visualizzare all'utente in risposta a questo codice di uscita.|  
|`FormatMessageFromSystem`|facoltativo. Determina se utilizzare il messaggio di errore fornito dal sistema corrispondente al codice di uscita oppure utilizzare il valore fornito in `String` . I valori validi sono `true` , che indica l'utilizzo dell'errore fornito dal sistema, e `false` , che indica l'utilizzo della stringa fornita da `String` . Il valore predefinito è `false`. Se questa proprietà è `false` , ma `String` non è impostata, verrà utilizzato l'errore fornito dal sistema.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente vengono definiti i comandi per l'installazione del .NET Framework 2,0.  
  
```  
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
 [Riferimento allo schema del prodotto e del pacchetto](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks> Elemento](../deployment/installchecks-element-bootstrapper.md)
