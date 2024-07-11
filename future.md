// //MAIN PAGE OF WEB SITE
// app.get(
//   "/listings",
//   wrapAsync(async (req, res) => {
//     const allListings = await Listing.find({});
//     res.render("../views/listings/index.ejs", { allListings });
//   })
// );

// //SHOW ROUTE

// app.get(
//   "/listings/:id",
//   wrapAsync(async (req, res) => {
//     let id = req.params.id;
//     const listing = await Listing.findById(id).populate("reviews");
//     res.render("../views/listings/show.ejs", { listing });
//   })
// );

// //NEW LISTING ADD
// app.get("/listings/new", (req, res) => {
//   res.render("../views/listings/newform.ejs");
// });

// app.post(
//   "/listings/new/add",
//   wrapAsync(async (req, res, next) => {
//     const data = req.body;
//     await Listing.insertMany(data);
//     res.redirect("/listings");
//   })
// );

// //TO EDIT THE POST
// app.get(
//   "/listings/edit/:id",
//   wrapAsync(async (req, res) => {
//     let id = req.params.id;
//     let data = await Listing.findById(id);
//     res.render("../views/listings/edit.ejs", { data });
//   })
// );

// app.put(
//   "/listings/:id/edit",
//   wrapAsync(async (req, res) => {
//     const id = req.params.id;
//     const newdata = req.body;
//     let data = await Listing.findByIdAndUpdate(id, newdata, { new: true });
//     res.redirect("/listings");
//     console.log(data);
//   })
// );

// //to DELETE THE DATA FROM THE LISTINGS
// app.delete(
//   "/listings/delete/:id",
//   wrapAsync(async (req, res) => {
//     const id = req.params.id;
//     let data = await Listing.findByIdAndDelete(id);
//     res.redirect("/listings");
//     console.log(data);
//   })
// );
// //MAIN PAGE OF WEB SITE
// app.get(
//   "/listings",
//   wrapAsync(async (req, res) => {
//     const allListings = await Listing.find({});
//     res.render("../views/listings/index.ejs", { allListings });
//   })
// );

// //SHOW ROUTE

// app.get(
//   "/listings/:id",
//   wrapAsync(async (req, res) => {
//     let id = req.params.id;
//     const listing = await Listing.findById(id).populate("reviews");
//     res.render("../views/listings/show.ejs", { listing });
//   })
// );

// //NEW LISTING ADD
// app.get("/listings/new", (req, res) => {
//   res.render("../views/listings/newform.ejs");
// });

// app.post(
//   "/listings/new/add",
//   wrapAsync(async (req, res, next) => {
//     const data = req.body;
//     await Listing.insertMany(data);
//     res.redirect("/listings");
//   })
// );

// //TO EDIT THE POST
// app.get(
//   "/listings/edit/:id",
//   wrapAsync(async (req, res) => {
//     let id = req.params.id;
//     let data = await Listing.findById(id);
//     res.render("../views/listings/edit.ejs", { data });
//   })
// );

// app.put(
//   "/listings/:id/edit",
//   wrapAsync(async (req, res) => {
//     const id = req.params.id;
//     const newdata = req.body;
//     let data = await Listing.findByIdAndUpdate(id, newdata, { new: true });
//     res.redirect("/listings");
//     console.log(data);
//   })
// );

// //to DELETE THE DATA FROM THE LISTINGS
// app.delete(
//   "/listings/delete/:id",
//   wrapAsync(async (req, res) => {
//     const id = req.params.id;
//     let data = await Listing.findByIdAndDelete(id);
//     res.redirect("/listings");
//     console.log(data);
//   })
// );




/REVIEWS
//POST ROUTE
app.post("/listings/:id/reviews", async (req, res) => {
  let listing = await Listing.findById(req.params.id);
  let newReview = new Review(req.body.review);
  console.log(newReview,req.body.review);
  listing.reviews.push(newReview);

  await newReview.save();
  await listing.save();

  res.redirect(`/listings/${listing._id}`);
});
// app.delete("listing/:id/reviews/:reviewId",wrapAsync(async(req,res)=>{
//   let {id,reviewId}=req.param;
//   await Listing.findByIdAndUpdate(id,{$pull:{reviews:reviewId}})
//  Review.findByIdAndDelete(reviewId)
//  redirect(`listing/${id}`)
// }))
app.delete("/review/:id/:id1", async(req, res)=>{
  const {id, id1} = req.params;

  await Review.findByIdAndDelete(id);

  res.redirect(`/listings/${id1}`)
})





// Create New Listing
// router.post(
//   "/new/add",
//   isLoggedIn,
//   validateListing,
//   wrapAsync(async (req, res)=>{
//     const newListing = new Listing(req.body.listing);
//     await newListing.save();
//     req.flash("success", "New listing created");
//     res.redirect("/listings");
//   })
// )



how to get secret code api key etc - Go to dashboard on Cloudinary
How to see cloudinary files--
Go to Media Library - you will see your folder
