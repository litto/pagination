# Pagination Library
Pagination for PHP project

## How to Install?

You can install it via composer by typing:-

composer require litto/pagination:v1.0

## How it Works?

After fetching records, Pass values through this
<?php
$cnt    =   $totalRecords/$limit;
$cnt    =   ceil($cnt);
$current    =   ($start/$limit)+1;  
 $count=round($totalRecords/$limit);
$pagenum=$start;
$pg =   new Pages();
$pages  =   $pg->getPages($current,$cnt,$limit);                    
$first  =   $pg->getFirst($cnt,$limit);
$last   =   $pg->getLast($cnt,$limit);
$prev   =   $pg->getPrev($current,$cnt,$limit);
$next   =   $pg->getNext($current,$cnt,$limit);

?>

Here $totalRecords signifies total records count 
$limit the limit count of trecords to display
After passing these values to Pages Function, this class will auto assign pages, first, last, prev next varibles which enable pagination to function

And in Page links Just put like:-

#### <ul>
											<li class="prev disabled">
												<a href="list.php?start=<?php echo $first;?>">
													<i class="icon-double-angle-left"></i>First
												</a>
											</li>
 <?php for($i=0;$i<count($pages);$i++){ 
                        $star   =   ($pages[$i]-1)*$limit;  ?>
											<li <?php if($start==$star){?> class="active" <?php }?>>
												<a href="list.php?start=<?php echo $star;?>"><?php echo $pages[$i];?></a>
											</li>
  <?php }?>
										

											<li class="next">
												<a href="list.php?startadd=<?php echo $last;?>">
													<i class="icon-double-angle-right"></i>Last
												</a>
											</li>
										</ul>

Now your paginations Links are generated
