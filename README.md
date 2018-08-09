# xml-to-ods-converter

beta xml to ods converter

include 'Converter.php';

$converter = new Converter;

$charset = ini_get('default_charset');
ini_set('default_charset', 'UTF-8');

$content = 'xml_path';

file_put_contents('save_path/content.xml',$content);
file_put_contents('save_path/mimetype','application/vnd.oasis.opendocument.spreadsheet');
file_put_contents('save_path/meta.xml',$converter->getMeta('es-ES'));
file_put_contents('save_path/styles.xml',$converter->getStyle());
file_put_contents('save_path/settings.xml',$converter->getSettings());
mkdir('save_path/META-INF/');
mkdir('save_path/Configurations2/');
mkdir('save_path/Configurations2/acceleator/');
mkdir('save_path/Configurations2/images/');
mkdir('save_path/Configurations2/popupmenu/');
mkdir('save_path/Configurations2/statusbar/');
mkdir('save_path/Configurations2/floater/');
mkdir('save_path/Configurations2/menubar/');
mkdir('save_path/Configurations2/progressbar/');
mkdir('save_path/Configurations2/toolbar/');
file_put_contents('save_path/META-INF/manifest.xml',$converter->getManifest());
shell_exec('cd save_path;zip -r '.escapeshellarg('ODS_TITTLE.ods').' ./');
ini_set('default_charset',$charset);
