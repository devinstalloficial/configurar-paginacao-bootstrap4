# config-links-pagination-bootstrap4

```
function configPagination($base_url, $total_rows, $per_page, $uri_segment)
  {
      return array(
          "base_url" => $base_url,
          "total_rows" => $total_rows,
          "per_page" => $per_page,
          "uri_segment" => $uri_segment,
          "next_link" => 'Próximo',
          "prev_link" => 'Anterior',
          "first_link" => false,
          "last_link" => false,
          "full_tag_open" => '<ul class="pagination justify-content-center">',
          "full_tag_close" => '</ul>',
          "attributes" => array("class" => 'page-link'),
          "first_tag_open" => '<li class="page-item">',
          "first_tag_close" => '</li>',
          "prev_tag_open" => '<li class="page-item">',
          "prev_tag_close" => '</li>',
          "next_tag_open" => '<li class="page-item">',
          "next_tag_close" => '</li>',
          "last_tag_open" => '<li class="page-item">',
          "last_tag_close" => '</li>',
          "cur_tag_open" => '<li class="page-item active"><span class="page-link">',
          "cur_tag_close" => '<span class="sr-only">(current)</span></span></li>',
          "num_tag_open" => '<li class="page-item">',
          "num_tag_close" => '</li>',
      );

  }
```

User Controller

```
class UserController extends CI_Controller {

	function configPagination($base_url, $total_rows, $per_page, $uri_segment){}

	function users()
	{

		$base_url = base_url() . "user";
		$total_rows = $this->user->countAll();
		$per_page = 10;
		$uri_segment = 2;

		$config = $this->configPagination($base_url, $total_rows, $per_page, $uri_segment);

		$this->pagination->initialize($config);

		$page = $this->uri->segment(2) ? $this->uri->segment(2) : 0;

		$data["users"] = $this->user->getAll($config["per_page"], $page);
		$data["links"] = $this->pagination->create_links();

		$this->load->view("user/index", $data);
		
	}
    
}
```

Model User

```
class User extends CI_Model
{

    private static $Table = "user";

    function getTableName()
    {
        return self::$Table;
    }

    function getAll($limit, $start)
    {
        return $this->db
            ->limit($limit, $start)
            ->get($this->getTableName())
            ->result();
    }

    function countAll()
    {
        return $this->db->count_all($this->getTableName());
    }

}
```

HTML list users

```
<div class="container mt-5">
    <h1>Users</h1>
    <table class="table table-sm table-striped">
        <thead>
            <tr>
                <th>Name</th>
            </tr>
        </thead>
        <tbody>
            <?php foreach($users as $user){ ?>
                <tr>
                    <td><?php echo $user->name; ?></td>
                </tr>
            <?php } ?>
        </tbody>
    </table>
    <div class="justify-conteny-center">
        <?php echo $links; ?>
    </div>

</div>
```
