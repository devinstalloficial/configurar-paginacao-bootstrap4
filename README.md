# config-links-pagination-bootstrap4

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
