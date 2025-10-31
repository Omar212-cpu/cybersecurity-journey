LAB 1 file upload vulnerabilities
solved this by capturing the request of the website were it took my image and changed the filename in the repeater to test.php ,
and changed the body to <?php echo file_get_contents('/home/carlos/secret') ?>
than i got the answer
