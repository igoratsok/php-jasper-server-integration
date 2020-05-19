# JasperServer Integration
JSIntegration for PHP quickly integrates node.js to Jasper Server and retrieves the binary data of the exported report.

# Usage
Usage is quite simple:
```php
require_once("jasperserverintegration.php");

// Create object
$jsi = new JasperServerIntegration(
    'http://localhost:8080/jasperserver',  // JasperServer URL
    'reports/aluno_escola_filtro',        // Report Unit Path
    'pdf',                                 // Report type
    'jasperadmin',                         // User
    'jasperadmin',                         // Password
    array("P_ALUNO_ID" => 1)
);

// Execute report.
try {
    $data = $jsi->execute();
    
    // Save to report.pdf
    $fp = fopen('report.pdf', 'w');
    fwrite($fp, $data);
    fclose($fp);
} catch(Exception $e) {
    print("Erro - $e->errorCode: $e->errorMessage.");
}

?>
```
