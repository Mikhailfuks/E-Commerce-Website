using System.ComponentModel.DataAnnotations;

namespace YourEcommerce.Models
{
    public class Product
    {
        [Key]
        public int Id { get; set; }

        [Required]
        public string Name { get; set; }

        [Required]
        public string Description { get; set; }

        [Required]
        public decimal Price { get; set; }

        public string ImageUrl { get; set; } // URL to product image
        public int QuantityInStock { get; set; }
    }
}
using Microsoft.AspNetCore.Mvc;
using YourEcommerce.Models;
using System.Collections.Generic;
using System.Linq;


namespace YourEcommerce.Controllers
{
    [ApiController]
    [Route("api/[controller]")] //API route for Products
    public class ProductsController : ControllerBase
    {
        //In a real application, you'd use a database context here
        private readonly List<Product> _products = new List<Product>();

        public ProductsController()
        {
            //Sample data - replace with database access
            _products.Add(new Product { Id = 1, Name = "T-Shirt", Description = "Cool T-shirt", Price = 19.99m, ImageUrl = "tshirt.jpg", QuantityInStock = 10 });
            _products.Add(new Product { Id = 2, Name = "Jeans", Description = "Stylish Jeans", Price = 49.99m, ImageUrl = "jeans.jpg", QuantityInStock = 5 });
        }

        [HttpGet]
        public ActionResult<IEnumerable<Product>> GetProducts()
        {
            return _products;
        }

        //Add other actions (POST for creating, PUT for updating, DELETE for deleting products)
    }
}
