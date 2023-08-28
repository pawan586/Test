# Test
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dynamic Top Menu</title>
<style>
  /* Add your CSS styles for the menu here */
  ul.navbar {
    list-style: none;
    display: flex;
    background-color: #333;
    padding: 10px;
  }
  ul.navbar li {
    margin-right: 20px;
  }
  ul.navbar li a {
    color: white;
    text-decoration: none;
  }
</style>
</head>
<body>
  <ul class="navbar">
    <script>
      const navbar = [
        { name: 'Home', id: 'home' },
        { name: 'About', id: 'about' },
        {
          name: 'Our Products',
          id: 'product',
          child: [
            { name: 'Product 1', id: 'p1' },
            { name: 'Product 2', id: 'p2' },
            { name: 'Product 3', id: 'p3' },
            { name: 'Product 4', id: 'p4' },
          ],
        },
        { name: 'Contact Us', id: 'contact' },
      ];

      const menuContainer = document.querySelector('.navbar');

      navbar.forEach(item => {
        const listItem = document.createElement('li');
        const link = document.createElement('a');
        link.href = `#${item.id}`;
        link.textContent = item.name;
        listItem.appendChild(link);

        if (item.child) {
          const subMenu = document.createElement('ul');
          item.child.forEach(childItem => {
            const subListItem = document.createElement('li');
            const subLink = document.createElement('a');
            subLink.href = `#${childItem.id}`;
            subLink.textContent = childItem.name;
            subListItem.appendChild(subLink);
            subMenu.appendChild(subListItem);
          });
          listItem.appendChild(subMenu);
        }

        menuContainer.appendChild(listItem);
      });
    </script>
  </ul>
</body>
</html>
